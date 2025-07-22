# Notes Kubernetes

1:16min

Kubernetes é um orquestrador de contêiners.
Usado para gerenciar e executar conteiners.
Atualmente é o padrão de mercado.

Para ambientes complexos:

- Escalabilidade
  - Escalar de forma vertical: Mais recurso computacional.
  - Escalar de forma horizontal: Multiplas instâncias/réplicas para distribuir/balancear as requisições.

- Resiliência

- Gerenciamento de ambientes e de atualizações
  - Microservices 
  - Várias aplicações

## Como funciona, como criar um cluster Kubernetes

Cluster é um conjunto de máquinas.
Kubernetes tem arquitetura pré-definida.
Podemos usar um kubernetes autogerenciado, ou seja, como serviço.

No cluster kubernetes, cada máquina vai exercer um dos dois papéis possíveis:

### 1. Control Plane
Orquestrador do cluster kubernetes.
Componentes:
- **API Server**: É a porta de entrada (ponto de comunicação) do cluster.
- **ETCD**: É um banco key-value. Todas as inf do cluster são armazenadas aqui, ele vai ter o estado do cluster.
   O API Server se comunica com o ETCD para fazer os registros das infs.
   As infs. nunca serão acessadas diretamente, sempre será via API Server.

- **Scheduler**: É responsável por endereçar as execuções dos conteiners.
   Ele analisa a especificação e defini/decidi qual Worker Node irá executar o conteiner.

- **Controller Manager**: Onde vai estar os controladores.
   Kubernetes trabalha baseado em estados, parametros.
   Qualquer alteração desses parametros vai ter um controlador para decidir o que deve ser feito.

   Ex: O parametros "Qtde de Nodes" alterou de 4 para 3, porque um node caiu, então um controlador vai ser acionado para tomar uma decisão, como por exemplo, colocar os containers para executar em outro worker node.


### 2. Worker Node
Responsável por executar os conteiners.
Componentes:
- **Kube-Proxy**: É responsável por fazer toda a comunicação de rede do cluster kubernetes.
- **Kubelet**: É responsável por garantir e solicitar a execução dos contêiners.
- **Container Runtime**: É responsável por realizar a execução do conatiner.
  
    A função do Kubelet é se comunicar com o Container Runtime para solicitar que ele faça a execução, e vai manter a comunicação para verificar frequentemente como está a execução dos containers e passar um feedback para o API Server para garantir que está tudo funcionando corretamente.

    Docker é um Container Runtime.
    Docker não é mais suportado pelo kubernetes como um Container Runtime, porque a comunicação entre o Kubelet e o Container Runtime acontece através do CRI (Container Runtime Interface), e o Docker não suporta o CRI.

    Outros Containers Runtime com suporte a CRI e Kubernetes:
    - ContainerD
    - CRI-O

    Docker tem um ótimo ecossitema para usar no terminal de trabalho, no dia a dia, para trabalhar de forma local.

    Docker, ContainerD e CRI-O usam o padrão OCI (Open Container Initiative), cujo objetivo é padronizar a construção de imagens e a execução de conteiners.
    Portanto, todos eles são compativeis entre si.
    Sendo assim, pode-se usar Docker localmente para trabalho e um dos outros para deploy com kubernetes sem problemas.

## Como usar

### 1. On-Premisse

Servidor próprio. Instalação e gerenciamento. controle total. exige conhecimento avançado.

### 2. Cloud

Kuberbetes as a Service.

- EKS
- AKS
- GKE

- Digital Ocean

### 3. Local

Ideal para estudos, mas não para ambiente de produção.
 
- Kind
- K3d

## References

- [digitalocean.com](digitalocean.com)