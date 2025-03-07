# Home

## 1. Introdução

O desafio 100 Days of Coding - Kubernetes é um plano estruturado para aprender Kubernetes de forma progressiva, abordando conceitos fundamentais, práticas avançadas e implementações reais.

O objetivo é permitir que qualquer pessoa adquira competências sólidas na orquestração de contêineres e na gestão de clusters Kubernetes.

## 2. Objetivo

Fornecer um guia prático de estudo diário para aprender Kubernetes, desde os conceitos básicos até implementações complexas em ambientes produtivos.

## 3. Público-Alvo

- Desenvolvedores
- Administradores de sistemas
- Engenheiros DevOps
- Arquitetos de software
- Qualquer profissional interessado em Kubernetes

## 4. Estrutura do Desafio

### 4.1. Fundamentos e Introdução ao Kubernetes

| Dia | Tema                                               | Tópicos                                         |
| --- | -------------------------------------------------- | ----------------------------------------------- |
| 1   | Introdução ao Kubernetes                           | O que é? Por que usá-lo? Casos reais            |
| 2   | Arquitetura do Kubernetes                          | API Server, etcd, Controller Manager, Scheduler |
| 3   | Instalando o Kubernetes                            | Minikube, Kind, Kubernetes no Docker            |
| 4   | Estrutura de um Pod                                | Criando e gerenciando Pods                      |
| 5   | Trabalhando com Labels e Annotations               | Organização no cluster                          |
| 6   | Namespaces no Kubernetes                           | Gerenciando ambientes isolados                  |
| 7   | Desafio: Criando seu primeiro ambiente             | Criar Pods e Namespaces do zero                 |
| 8   | Introdução a Deployments                           | Criando e gerenciando Deployments               |
| 9   | Replicasets                                        | Garantindo alta disponibilidade                 |
| 10  | Revisão e prática: Pods, Deployments e Replicasets | Exercícios de fixação                           |

### 4.2. Networking e Exposição de Aplicações

| Dia | Tema                                             | Tópicos                                      |
| --- | ------------------------------------------------ | -------------------------------------------- |
| 11  | Introdução a Services                            | Tipos de Services e como expor aplicações    |
| 12  | Ingress Controllers                              | Configurando regras de roteamento            |
| 13  | ConfigMaps e Secrets                             | Gerenciando configurações seguras            |
| 14  | Network Policies                                 | Controlando comunicação entre Pods           |
| 15  | Desafio: Criando uma aplicação com Ingress       | Criar um app com regras de roteamento        |
| 16  | RBAC no Kubernetes                               | Permissões e controle de acesso              |
| 17  | Revisão e prática: Networking e segurança básica | Exercícios práticos                          |
| 18  | Criando um cluster Kubernetes                    | Configuração com kubeadm                     |
| 19  | Deploy de aplicações reais                       | Subindo um app completo                      |
| 20  | Desafio: Troubleshooting de deploy               | Resolver problemas de uma aplicação quebrada |

### 4.3. Armazenamento e Gerenciamento de Estado

| Dia | Tema                                           | Tópicos                                   |
| --- | ---------------------------------------------- | ----------------------------------------- |
| 21  | Introdução a Volumes                           | Persistência de dados no Kubernetes       |
| 22  | Persistent Volumes e Claims                    | Como funciona o armazenamento             |
| 23  | StatefulSets                                   | Gerenciando aplicações com estado         |
| 24  | Dynamic Provisioning de Volumes                | Automação de armazenamento                |
| 25  | Desafio: Criando um banco de dados persistente | Criar um StatefulSet para PostgreSQL      |
| 26  | Storage avançado                               | CSI (Container Storage Interface)         |
| 27  | Revisão e prática: Storage no Kubernetes       | Exercícios de fixação                     |
| 28  | Desafio: Troubleshooting de storage            | Resolver um problema de PVC que não monta |
| 29  | Introdução ao Helm                             | Automação com pacotes Kubernetes          |
| 30  | Desafio: Criando um Helm Chart do zero         | Pacotizar e versionar uma aplicação       |

### 4.4. Monitoramento e Observabilidade

| Dia | Tema                                           | Tópicos                                         |
| --- | ---------------------------------------------- | ----------------------------------------------- |
| 31  | Configuração de Logs                           | Logs de Pods e Services                         |
| 32  | Monitoramento com Prometheus                   | Instalando e configurando                       |
| 33  | Visualização com Grafana                       | Criando dashboards                              |
| 34  | Debugging no Kubernetes                        | Identificando e corrigindo erros                |
| 35  | Kubernetes Events                              | Entendendo eventos no cluster                   |
| 36  | Desafio: Criando um monitoramento completo     | Implementar observabilidade com logs e métricas |
| 37  | Tracing com OpenTelemetry                      | Monitorando requests entre serviços             |
| 38  | Logging avançado                               | Loki e Fluentd                                  |
| 39  | Desafio: Troubleshooting de observabilidade    | Resolver um problema de logs/métricas           |
| 40  | Revisão e prática: Monitoramento no Kubernetes | Exercícios práticos                             |

### 4.5. Autoscaling, Jobs e CI/CD

| Dia | Tema                                            | Tópicos                                      |
| --- | ----------------------------------------------- | -------------------------------------------- |
| 41  | Trabalhando com Jobs e CronJobs                 | Execução de tarefas programadas              |
| 42  | Autoscaling no Kubernetes                       | Configurando HPA (Horizontal Pod Autoscaler) |
| 43  | Criando uma CI/CD com Kubernetes                | Pipeline básico de deploy                    |
| 44  | ArgoCD                                          | Deploy declarativo com GitOps                |
| 45  | GitOps com Flux                                 | Gerenciando versões no Kubernetes            |
| 46  | Desafio: Criando um pipeline completo           | CI/CD + deploy automático                    |
| 47  | Estratégias de Deploy                           | Blue/Green, Canary e Rolling Updates         |
| 48  | Kubernetes Probes                               | Liveness, Readiness e Startup Probes         |
| 49  | Desafio: Implementando rollback e health checks | Configurar rollback seguro                   |
| 50  | Revisão e prática: Deploy e escalabilidade      | Exercícios práticos                          |

### 4.6. Segurança e Alta Disponibilidade

| Dia | Tema                                       | Tópicos                              |
| --- | ------------------------------------------ | ------------------------------------ |
| 51  | Políticas de segurança                     | Pod Security Standards (PSS)         |
| 52  | Trabalhando com Webhooks                   | Admission Controllers                |
| 53  | Ferramentas de auditoria                   | Falco e kubeaudit                    |
| 54  | Kubernetes e Service Meshes                | Istio, Linkerd, Consul               |
| 55  | Configuração de TLS no Kubernetes          | Certificados e segurança             |
| 56  | Desafio: Criando uma política de segurança | Configurar PSS e RBAC                |
| 57  | Kubernetes API Extensions                  | API Aggregation Layer                |
| 58  | Custom Resource Definitions (CRDs)         | Criando recursos personalizados      |
| 59  | Operators no Kubernetes                    | Automatizando tarefas complexas      |
| 60  | Desafio: Criando um Operator simples       | Criar um Operator para uma aplicação |

### 4.7. Kubernetes Avançado e Projeto Final

| Dia | Tema                                    | Tópicos                        |
| --- | --------------------------------------- | ------------------------------ |
| 61  | Multi-tenancy no Kubernetes             | Isolamento e segurança         |
| 62  | Kubernetes Federation                   | Gerenciando múltiplos clusters |
| 63  | Kubernetes no Edge Computing            | Projetos reais                 |
| 64  | Kubernetes e Serverless                 | Knative e OpenFaaS             |
| 65  | Kubernetes e IA                         | TensorFlow on Kubernetes       |
| 66  | Desafio: Kubernetes em ambiente híbrido | Criar um cluster multi-cloud   |
| 67  | Kubernetes para workloads Windows       | Containers Windows             |
| 68  | Kubernetes no 5G                        | Aplicações e desafios          |
| 69  | Desafio: Kubernetes em produção         | Configuração avançada para HA  |

### 4.8. Kubernetes na Prática: Preparação para o Projeto Final

| Dia | Tema                                       | Tópicos                                              |
| --- | ------------------------------------------ | ---------------------------------------------------- |
| 70  | Revisão: Kubernetes para produção          | Checklist de um cluster real                         |
| 71  | Estratégias avançadas de deploy            | Blue/Green, Canary, Rolling Updates                  |
| 72  | Trabalhando com Sidecars e Init Containers | Melhores práticas e casos de uso                     |
| 73  | Kubernetes Probes                          | Configuração de Liveness, Readiness e Startup Probes |
| 74  | Pod Disruption Budgets                     | Mantendo alta disponibilidade                        |
| 75  | Trabalhando com Webhooks no Kubernetes     | Admission Controllers                                |
| 76  | Kubernetes Gateway API vs Ingress          | Diferenças e futuro                                  |
| 77  | Revisão: Segurança no Kubernetes           | Práticas essenciais para clusters seguros            |
| 78  | Configuração de DNS no Kubernetes          | CoreDNS e coredns-custom                             |
| 79  | Revisão: Troubleshooting avançado          | Exercícios práticos de debug                         |

### 4.9. Kubernetes e Aplicações Modernas

| Dia | Tema                                    | Tópicos                            |
| --- | --------------------------------------- | ---------------------------------- |
| 80  | Kubernetes e Big Data                   | Spark on Kubernetes                |
| 81  | Kubernetes e WebAssembly                | WASM em contêineres                |
| 82  | Kubernetes e IoT                        | Orquestração de dispositivos       |
| 83  | Kubernetes e Blockchain                 | Casos de uso reais                 |
| 84  | Kubernetes e Web3                       | Infraestrutura descentralizada     |
| 85  | Kubernetes e FinOps                     | Redução de custos na nuvem         |
| 86  | Revisão: Kubernetes para microsserviços | Estratégias recomendadas           |
| 87  | Kubernetes para aplicações monolíticas  | Viabilidade e desafios             |
| 88  | Kubernetes Federation                   | Gerenciamento multi-cloud avançado |
| 89  | Kubernetes para redes 5G                | Deploy de aplicações críticas      |

### 4.10. Kubernetes em Produção

| Dia   | Tema                                             | Tópicos                                          |
| ----- | ------------------------------------------------ | ------------------------------------------------ |
| 90    | Revisão: Armazenamento no Kubernetes             | Comparação de opções e melhores práticas         |
| 91    | Revisão: Segurança em ambientes multi-cloud      | Kubernetes federado                              |
| 92    | Kubernetes no Edge Computing                     | Desafios reais e melhores práticas               |
| 93    | Ferramentas para Kubernetes nativo               | Lens, Octant, Portainer                          |
| 94    | Kubernetes e redes definidas por software (SDN)  | Cilium, Calico                                   |
| 95    | Trabalhando com Webhooks e Admission Controllers | Políticas customizadas                           |
| 96    | Kubernetes e Service Meshes                      | Comparação: Istio, Linkerd, Consul               |
| 97    | Gerenciamento de custos no Kubernetes            | Kubecost e OpenCost                              |
| 98    | Criando clusters efêmeros                        | Terraform e Kubernetes                           |
| 99    | Revisão final: Kubernetes em Produção            | Checklist e boas práticas                        |
| 100 ~ | Projeto Final                                    | Criar um cluster Kubernetes completo e otimizado |

## 5. Guia de Uso

1. Siga a ordem sugerida, estudando um tópico por dia.
2. Pratique cada conceito implementando no Kubernetes.
3. Utilize a documentação oficial e cursos complementares.
4. Participe de comunidades e discuta desafios diários.
5. Documente seu progresso em um blog ou GitHub.

## 6. Referências

- [Documentação oficial do Kubernetes](https://kubernetes.io/docs/)
- [Kubernetes The Hard Way - Kelsey Hightower](https://github.com/kelseyhightower/kubernetes-the-hard-way)
- [Certificação Kubernetes CKA e CKAD](https://www.cncf.io/certification/)
