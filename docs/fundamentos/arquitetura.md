# Arquitetura

## 1. Introdução

O Kubernetes é uma plataforma de orquestração de contêineres open-source amplamente adotada para gerenciar aplicações em contêineres de forma escalável, resiliente e automatizada. Ele abstrai a infraestrutura subjacente e fornece uma interface declarativa para definir, implantar e gerenciar aplicações distribuídas.

## 2. Objetivo

Este documento detalha a arquitetura do Kubernetes, explicando seus principais componentes, funcionamento interno e como os diferentes elementos interagem para fornecer alta disponibilidade, escalabilidade e automação.

## 3. Público-Alvo

Este documento é voltado para desenvolvedores, engenheiros de DevOps, administradores de sistemas e arquitetos de software que desejam aprofundar seu conhecimento sobre a estrutura do Kubernetes.

## 4. Arquitetura Geral

O Kubernetes segue um modelo baseado em **cluster**, onde um conjunto de nós trabalham em conjunto para executar e gerenciar aplicações. A arquitetura pode ser dividida em dois grandes grupos:

### 4.1. Plano de Controle (Control Plane)

O plano de controle é responsável por gerenciar o estado do cluster, garantindo que as aplicações e serviços estejam em conformidade com as definições desejadas. Ele é composto por diversos componentes que trabalham em conjunto para coordenar as operações do cluster.

#### 4.1.1 API Server

O API Server é o principal ponto de entrada para a comunicação com o Kubernetes. Ele expõe uma API RESTful que recebe e processa todas as solicitações, sejam elas de usuários, componentes internos ou ferramentas automatizadas.

!!! info "Problema que resolve"
    O API Server resolve o problema de gerenciamento centralizado, permitindo que diferentes clientes e componentes interajam com o cluster de forma padronizada.

##### Como interagir com o API Server

A interação com o API Server pode ser feita por meio da **kubectl**, que é a ferramenta de linha de comando oficial, ou diretamente via chamadas REST.

Exemplo de requisição REST:

```bash
curl -X GET https://<API_SERVER>/api/v1/nodes -H "Authorization: Bearer <TOKEN>"
```

#### 4.1.2 Etcd

O etcd é um banco de dados distribuído que armazena o estado do cluster. Ele mantém informações sobre nós, pods, serviços, políticas de rede e demais configurações.

!!! warning "Importância do etcd"
    Se o etcd falhar, o cluster pode ficar inconsistente e até inoperável. Por isso, ele deve ser altamente disponível e devidamente replicado.

##### Como interagir com o etcd

O etcd pode ser acessado diretamente via **etcdctl**, a ferramenta de linha de comando oficial.

Exemplo de consulta ao etcd:

```bash
etcdctl get /registry/pods --prefix --keys-only
```

#### 4.1.3 Controller Manager

O Controller Manager é responsável por executar vários controladores que monitoram o estado do cluster e realizam as ações necessárias para mantê-lo conforme definido.

!!! info "Problema que resolve"
    Sem um mecanismo de controle, o Kubernetes não teria como garantir que os objetos do cluster estejam sempre no estado desejado.

##### Como interagir com o Controller Manager

O Controller Manager opera de maneira autônoma e não expõe uma API direta, mas seu funcionamento pode ser monitorado através de logs e métricas no API Server.

Exemplo de verificação de logs:

```bash
kubectl logs -n kube-system kube-controller-manager-<id>
```

#### 4.1.4 Scheduler

O Scheduler é o componente que decide em quais nós os pods serão alocados com base em critérios como disponibilidade de recursos, afinidade, restrições de localização e políticas do cluster.

!!! tip "Agendamento eficiente"
    O agendamento eficiente é essencial para garantir um uso balanceado dos recursos e evitar gargalos de desempenho.

##### Como interagir com o Scheduler

O Scheduler também opera de forma automática e não possui uma API exposta diretamente, mas é possível verificar o funcionamento e logs via **kubectl**.

Exemplo de análise dos logs do Scheduler:

```bash
kubectl logs -n kube-system kube-scheduler-<id>
```

### 4.2. Nodos de Trabalho (Worker Nodes)

Os Worker Nodes são responsáveis por executar as cargas de trabalho dentro do cluster. Cada nó de trabalho executa os pods, que são os menores componentes executáveis de uma aplicação.

#### 4.2.1 Kubelet

O Kubelet é um agente que roda em cada Worker Node e é responsável por garantir que os contêineres dos pods sejam executados corretamente. Ele se comunica com o API Server para receber comandos e enviar atualizações do estado do nó.

!!! info "Problema que resolve"
    Sem o Kubelet, o Kubernetes não teria como garantir que os pods estejam sempre rodando conforme esperado nos nós de trabalho.

##### Como interagir com o Kubelet

O Kubelet pode ser acessado localmente no nó através de sua API.

Exemplo de requisição:

```bash
curl -s http://localhost:10255/pods
```

#### 4.2.2 Container Runtime

O Container Runtime é o software que executa os contêineres dentro do nó. O Kubernetes é compatível com diversos runtimes, como Docker, containerd e CRI-O.

!!! warning "Escolha do runtime"
    A escolha do runtime pode impactar a performance, a segurança e a compatibilidade do cluster.

##### Como interagir com o Container Runtime

A interação depende do runtime utilizado. No caso do **containerd**, pode-se usar **ctr**:

```bash
ctr -n k8s.io containers list
```

#### 4.2.3 Kube Proxy

O Kube Proxy gerencia a comunicação dentro do cluster, garantindo que os serviços possam se comunicar entre si de forma transparente, independentemente do nó onde estão sendo executados.

!!! info "Problema que resolve"
    Sem o Kube Proxy, os pods não conseguiriam se comunicar corretamente dentro do cluster, tornando inviável a execução de aplicações distribuídas.

##### Como interagir com o Kube Proxy

O Kube Proxy opera automaticamente, mas seus logs podem ser inspecionados:

```bash
kubectl logs -n kube-system kube-proxy-<id>
```

## 5. Comunicação Interna do Kubernetes

Os componentes do Kubernetes se comunicam por meio de API endpoints, usando gRPC ou RESTful HTTP. O etcd armazena todos os estados do cluster, e os componentes do plano de controle interagem com ele constantemente para garantir a consistência dos dados.

### 5.1. Comunicação entre API Server e etcd

- O API Server lê e escreve estados no etcd utilizando chamadas seguras com TLS.
- Todos os componentes do plano de controle acessam o etcd para garantir que o estado do cluster esteja sempre atualizado.

### 5.2. Comunicação entre o API Server e os Worker Nodes

- O API Server envia comandos para os kubelets nos nós de trabalho.
- Os Worker Nodes reportam status ao API Server regularmente.

## 6. Modelos de Deploy do Kubernetes

O Kubernetes pode ser implantado de várias formas, dependendo da necessidade da organização:

- **Bare Metal**: Instalação direta em servidores físicos sem virtualização.
- **Cloud-Managed Kubernetes**: Soluções gerenciadas como Google Kubernetes Engine (GKE), Amazon EKS e Azure AKS.
- **Kubernetes On-Premises**: Executado em infraestrutura privada com ferramentas como kubeadm ou OpenShift.

## 7. Segurança no Kubernetes

O Kubernetes implementa várias camadas de segurança para proteger os recursos e aplicações:

- **RBAC (Role-Based Access Control)**: Define permissões de acesso granularizadas.
- **Network Policies**: Controlam a comunicação entre pods e serviços.
- **Pod Security Policies**: Restringem permissões e capacidades dos contêineres.
- **TLS e Certificados**: Comunicação segura entre componentes.

## 8. Monitoramento e Logging

Para manter a observabilidade do cluster, o Kubernetes suporta diversas ferramentas de monitoramento e logging:

- **Prometheus**: Coleta métricas do cluster e dos pods.
- **Grafana**: Exibe dashboards de métricas coletadas.
- **Fluentd**: Agrega logs de contêineres para centralização.

## 9. Escalabilidade no Kubernetes

O Kubernetes suporta escalabilidade horizontal e vertical de aplicações:

- **Horizontal Pod Autoscaler (HPA)**: Ajusta automaticamente o número de réplicas de um pod com base em métricas de uso.
- **Vertical Pod Autoscaler (VPA)**: Ajusta os recursos (CPU e memória) dos pods dinamicamente.
- **Cluster Autoscaler**: Ajusta a quantidade de nós no cluster conforme a demanda.

## 10. Referências

- [Documentação Oficial do Kubernetes](https://kubernetes.io/docs/)
- [CNCF - Cloud Native Computing Foundation](https://www.cncf.io/)
- [Guia de Administração do Kubernetes](https://kubernetes.io/docs/setup/)
