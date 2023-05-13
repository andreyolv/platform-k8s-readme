# platform-k8s-readme

![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/6fc9b07c-f73e-4588-8efa-f6d708722e1c)

## Estrutura do Repositório
![image](https://user-images.githubusercontent.com/49295662/233882124-ee8faaf7-7e6a-44a9-9cec-48dcc1e130d8.png)

Esse é meu repositório unico para fazer POCs de diversas tecnologias e projetos. Grande parte do meu conhecimento está compilado aqui.

É um cluster local, e utilizo o kind para subir o cluster:
```sh 
kind create cluster --name platform-k8s --config kind-config.yaml
```

Explicação e organização dos diretórios:
- clusters:
Uso um arquivo Kustomization que passa os recursos/tecnologias que quero subir, e elas apontam para os diretórios que estão em infrastructure. Isso torna o cluster  completamente modular e simples de escolher o que fazer deploy. 

- data-projects:
POCs de projetos de dados.

- devops-projects:
POCs de projetos de devops.

- docker:
Imagens bases para projetos estruturantes.

- docs:
Documentações, templates de arquivos, mapas mentais de estudos, materiais de aulas.

- infrastructure:
HelmCharts e deployments das tecnologias no kubernetes.

## GitOps | Flux

Utilizo o Flux como ferramenta de GitOps para sincronizar todos os HelmCharts

Sync the repository in the kubernetes cluster using Flux, replace variables GITHUB_USER and GITHUB_REPO:

You will need to create a [PAT (Personal Access Token)(Classic)](https://github.com/settings/tokens), check repo and users, and save the Github Token.

```sh 
flux bootstrap github \
  --owner=GITHUB_USER \
  --repository=GITHUB_REPO \
  --branch=main \
  --path=./clusters/dev \
  --personal
```

# BIG DATA & DEVOPS PLATFORM ON KUBERNETES CONTAINS:

# CI/CD & IaC
## crossplane
## tekton
## terraform

# Compliance
## kyverno
Contém UI policy-reporter

## sonarqube

# Data Engineering
## airbyte
## airflow
## minio
Integrado com spark no jupyter notebook
Integrado com velero
Integrado com delta / lakehouse
Integrado para logs do spark history server

## openfaas
## spark
## superset
## trino
Conectado no MinIO/S3, falta testar uma query

# Databases
![image](https://user-images.githubusercontent.com/49295662/233882435-5fc3ac18-5e2e-46b2-8b50-68e4f6834b1b.png)

cassandra
mongodb
mysql
postgresql
redis
yugabytedb


# Orchestration
## harbor
Login e senha não funciona, verificar

## kaniko
Lê um Dockerfile do meu repositório privado do github. builda a imagem dentro do kubernetes e envia para minha conta do Dockerhub

## keda
##linkerd
Gera certificados do tipo selfsigned pelo Cert-manager, 
Implementa control plane, linkerd-viz, linkerd-multicluster

linkerd-jaeger não está maduro suficiente

portainer
rancher

# Security
## cert-manager
Integrado com o Linkerd, gerando ClusterIssuer selfsigned. Certificate e Issuer.
Como é selfsigned não precisa de uma CA (Autoridade Certificadora)

falco
kube-bench
kubescape
teleport
trivy

# Streaming
kafka
ksqldb
pinot
rabbitmq


