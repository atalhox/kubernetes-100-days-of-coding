# Instalação

## 1. Introdução

O Kubernetes é uma plataforma de orquestração de contêineres que permite gerenciar cargas de trabalho e serviços de maneira automatizada.

Para desenvolvedores e operadores que desejam testar e desenvolver aplicações em Kubernetes, existem diferentes opções para rodá-lo localmente, incluindo Minikube, Kind e Kubernetes no Docker.

Este documento apresenta um guia detalhado para instalação e configuração dessas ferramentas.

## 2. Objetivo

Este guia tem como objetivo fornecer instruções passo a passo para a instalação do Kubernetes localmente utilizando Minikube, Kind e Kubernetes no Docker, permitindo um ambiente de testes funcional para desenvolvedores e administradores de sistemas.

## 3. Público-Alvo

- Desenvolvedores que desejam testar aplicações em um cluster Kubernetes local.
- Administradores de sistemas e DevOps que precisam de um ambiente para experimentação.
- Estudantes e entusiastas de tecnologia que querem aprender sobre Kubernetes.

## 4. Pré-requisitos

Antes de iniciar a instalação, verifique se seu sistema atende aos seguintes requisitos:

| Recurso             | Requisito                               |
| ------------------- | --------------------------------------- |
| Sistema Operacional | Linux, macOS ou Windows                 |
| Processador         | Arquitetura x86-64                      |
| Memória RAM         | Mínimo de 4 GB (recomendado 8 GB)       |
| Virtualização       | Ativada na BIOS (para Minikube)         |
| Docker              | Versão mais recente instalada           |
| Kubectl             | Instalado para gerenciamento do cluster |

**O que é Kubernetes?**

Kubernetes é um sistema de código aberto para automação de implantação, dimensionamento e gerenciamento de aplicações em contêineres.

## 5. Comparando Minikube, Kind e Kubernetes no Docker

| Ferramenta                         | Vantagens                                                                                         | Desvantagens                                                                        |
| ---------------------------------- | ------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| **Minikube**                       | Fácil de usar, suporte nativo ao Kubernetes, diversas opções de drivers (Docker, VirtualBox, KVM) | Pode ser pesado para máquinas com pouca memória                                     |
| **Kind**                           | Rápido, leve, ótimo para CI/CD, executa clusters dentro de contêineres Docker                     | Pode não suportar alguns recursos nativos do Kubernetes como balanceadores de carga |
| **Kubernetes no Docker (K3s/k0s)** | Leve, ideal para testes rápidos e ambientes de desenvolvimento                                    | Nem sempre reflete um ambiente de produção real                                     |

## 6. Instalando o Kubernetes Localmente

### 6.1. Instalando o Minikube

#### 6.1.1. O que são os famosos Drivers?

Os drivers definem como o cluster Kubernetes será executado e qual tecnologia será usada para criar e gerenciar os nós do cluster.

**Como os drivers funcionam?**

- Criam o ambiente adequado para rodar o Kubernetes.
- Alocam recursos como CPU, memória e rede.
- Garantem a comunicação entre os nós.
- Criam ambientes isolados para evitar conflitos com outras aplicações.

#### 6.1.2. Drivers do Minikube

| Driver                | Descrição                                         | Quando Usar?                                                                          |
| --------------------- | ------------------------------------------------- | ------------------------------------------------------------------------------------- |
| **Docker**            | Usa o Docker como backend para rodar o Kubernetes | Recomendado para quem já tem Docker instalado e deseja evitar máquinas virtuais       |
| **VirtualBox**        | Utiliza VirtualBox para criar a VM do cluster     | Ideal para usuários que não têm suporte nativo ao Docker ou querem isolar o ambiente  |
| **KVM**               | Usa o Kernel-based Virtual Machine (KVM) no Linux | Melhor desempenho em sistemas Linux com suporte a virtualização                       |
| **Hyperkit**          | Driver para macOS baseado em Hypervisor.framework | Alternativa leve para usuários de macOS                                               |
| **None (bare-metal)** | Roda diretamente no host sem máquinas virtuais    | Para usuários avançados que querem instalar Kubernetes diretamente sem camadas extras |

#### 6.1.3. Instalando o Minikube

**Linux:**
```sh
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

**macOS:**
```sh
brew install minikube
```

**Windows (Chocolatey):**
```sh
choco install minikube
```

#### 6.1.4. Iniciando o Minikube com um Driver Específico

```sh
minikube start --driver=docker
```

Ou, para rodar com VirtualBox:
```sh
minikube start --driver=virtualbox
```

Para verificar o status do cluster:
```sh
minikube status
```

### 6.2. Instalando o Kind

O Kind (Kubernetes in Docker) permite criar clusters Kubernetes dentro de contêineres Docker, sendo ideal para testes e CI/CD.

#### 6.2.1. Como o Kind gerencia os nós do cluster?

- Cada nó do Kubernetes é um contêiner Docker.
- O ambiente é automaticamente configurado com os componentes necessários.
- O plano de controle e os nós são separados em contêineres distintos.

#### 6.2.2. Instalando o Kind

**Linux:**
```sh
curl -Lo ./kind https://kind.sigs.k8s.io/dl/latest/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```

**macOS:**
```sh
brew install kind
```

#### 6.2.3. Criando um Cluster com Kind

```sh
kind create cluster --name meu-cluster
```

Verificar se o cluster está rodando:
```sh
kubectl cluster-info --context kind-meu-cluster
```

## 7. Referências

- [Documentação Oficial do Kubernetes](https://kubernetes.io/docs/)
- [Guia Oficial do Minikube](https://minikube.sigs.k8s.io/docs/)
- [Projeto Kind no GitHub](https://kind.sigs.k8s.io/)
- [K3s – Kubernetes Lightweight](https://k3s.io/)
- [k0s – Kubernetes Simplificado](https://k0sproject.io/)

