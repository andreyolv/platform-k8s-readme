# platform-k8s-readme

![k8s-platform](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/a59b7812-e2d9-47d7-929f-d4e135942245)

## Estrutura do Repositório

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
# Development
## Autoscaling
- KEDA

## Message Queueing
- RabbitMQ
  
## Serverless Functions
- OpenFaas
  
---------------------------------------------------------------------

# DevOps

## Images
- Docker

- Kaniko
  - :heavy_check_mark: Lê um Dockerfile do meu repositório privado do github.
  - :heavy_check_mark: Builda a imagem dentro do kubernetes e envia para minha conta do Dockerhub

- Harbor

## Version Control
- Git

- Github
  - :heavy_check_mark: Regras para distribuição automática de Pull Request para os codeowners específicos.

## Templating
- Helm

- Kustomize
  - :heavy_check_mark: Realizar testes exemplos da documentação para entender possibilidades.

## CI/CD
- Github Actions
  - :heavy_check_mark: Automatização para build de imagem docker e envio para container registry.
  - :heavy_check_mark: Testes de validação de Pull Request.

## Infrastructure as Code
- Crossplane
  - :hourglass_flowing_sand: Integrar com Azure.
    
## GitOps
- Flux
  - :heavy_check_mark: Contém Flux-UI.
  - :hourglass_flowing_sand: Adicionar automação com imagens.
  - :hourglass_flowing_sand: Estudar parte de notificações.

## Policies
- Kyverno
  - :heavy_check_mark: Contém UI policy-reporter.

- Gatekeeper
  - :heavy_check_mark: Realiza mutação de campos específicos nos YAML dos pods na hora da criação deles.

- Datree
  - :hourglass_flowing_sand: Adicionar no Github Actions como teste de Pull Request.

## Disaster Recovery
- Velero
  - :heavy_check_mark: Integrar com MinIO (S3 Bucket da AWS).
  - :heavy_check_mark: Integrar com Blob Storage da Azure.
  - :heavy_check_mark: Backups, restores e schedules aplicados atráves dos yamls CRD's do Velero para sincronia com GitOps e manter histórico no Github.

## Cost
- Kubecost
  - :heavy_check_mark: Integrar com Azure.
    
## Ingress Controller
- Nginx

## Storage
- MinIO
  - :heavy_check_mark: Integrar com spark no jupyter notebook, Velero, Delta, logs do spark history server.
  - :hourglass_flowing_sand: Criar operator no kubernetes para facilitar mock de dados.

- Longhorn

## Service Mesh
- Linkerd
  - :heavy_check_mark: Instalar CRDs antes do Helm Chart do Control Plane.
  - :heavy_check_mark: Criar certificados através do Cert-Manager.
  - :heavy_check_mark: Habilitar o Linkerd Control Plane passandos os certificados.
  - :heavy_check_mark: Habilitar o Linkerd Viz, uma interface web de usuário para melhor visualizar.
  - :heavy_check_mark: Realizar Proxy Injectio nos namespaces que serão habilitados o Service Mesh.
  - :heavy_check_mark: Expor métricas do Linkerd Viz para o Promethes, pois o default do Linkerd-Viz é de apenas 6 horas.
  - :heavy_check_mark: Habilitar o Linkerd Multicluster para interconectividade entre cluster Kubernetes.
  - :hourglass_flowing_sand: Criar conexão entre 2 clusters com o Linkerd Multicluster.
  - :hourglass_flowing_sand: Habilitar o Linkerd Jaeger para adicionar funcionalidade de tracing.

- Cilium
  - :hourglass_flowing_sand: Integrar com Azure CNI Chaining.
  - :hourglass_flowing_sand: Habilitar Hubble.
  - :hourglass_flowing_sand: Habilitar Cilium Mesh.

## Troubleshooting
- Komodor

## Cluster Management
- Rancher

## Code Quality
- SonarQube

## API Gateway
- Kong
  - :heavy_check_mark: Habilitar Postgresql no Chart na versão 11, pois acima da 12 não funciona para integrar com o Konga.
  - :heavy_check_mark: Habilitar o Konga, uma interface web de usuário para facilitar as configurações no Kong.

---------------------------------------------------------------------

# Data

## SQL Databases
- MySQL

- PostgreSQL
  - :hourglass_flowing_sand: Criar operator no kubernetes para facilitar mock de dados.

## NoSQL Databases
- MongoDB
  - :hourglass_flowing_sand: Criar operator no kubernetes para facilitar mock de dados.

- Redis

- Cassandra

- Neo4j
  - :hourglass_flowing_sand: Precisa de certificados para subir o helm chart certo.

## Orchestration
- Airflow

## Processing
- Spark
  - :heavy_check_mark: Habilitar Spark Operator
  - :hourglass_flowing_sand: Integrar as SparkApplications como Tasks no Airflow.
  - :hourglass_flowing_sand: Habilitar Spark History Server para centralizar logs das execuções do PySpark.

- Flink
  - :hourglass_flowing_sand: Realizar POC.

- ksqldb
  - :heavy_check_mark: Integrar com ecossistema do Kafka. (com TLS habilitado)

## Lakehouse
- Delta
  - :hourglass_flowing_sand: Integrar com Spark Operator.

## Query Engine
- Trino
  - :hourglass_flowing_sand: Integrar com autenticação do Azure Active Directory, porém precisa editar helm chart para passar parâmetros necessários.

## Machine Learning
- Mlflow
  - :heavy_check_mark: Integrar acesso da url de acesso do ingress com OAuth2.

## Viz
- Superset
  - :heavy_check_mark: Habilitado.

## Integration
- Airbyte
  - :hourglass_flowing_sand: Realizar POC.

## Streaming
- Kafka
  - :heavy_check_mark:

- Redpanda
  - :hourglass_flowing_sand: Realizar POC.
  - :hourglass_flowing_sand: Habilitar Redpanda Console.

## Lineage
- OpenLineage
  - :heavy_check_mark: Integrar com PySpark.
  - :hourglass_flowing_sand: Enviar dados do PySpark para o Kafka.
  - :hourglass_flowing_sand: Enviar dados do Pyspark para o Marquez via API.

- Marquez
 - :hourglass_flowing_sand: O Input dos dados é apenas via API

## OLAP
- Pinot
  - :hourglass_flowing_sand: Realizar POC.

- Clickhouse
  - :hourglass_flowing_sand: Realizar POC.

## Change Data Capture
- Debezium
  - :heavy_check_mark: Habilitado em MySQL
  - :heavy_check_mark: Habilitado em SQLServer
 
## Catalog
- Datahub
  - :hourglass_flowing_sand: Uma bosta pra subir isso aqui.

---------------------------------------------------------------------

# Observability

## Collector
- fluentd
  - :heavy_check_mark: DaemonSet que coleta logs de todos os containers em todos os pods do cluster e envia para o ElasticSearch.

## Logs
- ElasticSearch
  - :heavy_check_mark: Repositório central de logs do cluster.
  - :heavy_check_mark: Rotina de Curator para limpeza de logs antigos.

## Metrics
- Prometheus

## Alerts
- Robusta
  - :heavy_check_mark: Notificações enviadas para meu Telegram.

## Dashboards
- Grafana
  - :heavy_check_mark: Dashboards para monitoramento de kubernetes, airflow, change data capture em bancos sqlserver, kafka (strimzi), kubecost, velero, flux.
  - :heavy_check_mark: Gerenciamento de alertas para falhas no Kafka (Strimzi) e Velero.

- Kibana
  - :heavy_check_mark: Interface web para buscas de logs usando KQL (Kibana Query Language).

## Tracing
- Jaeger
  - :hourglass_flowing_sand: Realizar POC.

## Chaos Engineering
- Litmus
  - :hourglass_flowing_sand: Realizar POC.
  
---------------------------------------------------------------------

# Security

## Certificates
- cert-manager
  - :heavy_check_mark: Integrar com o Linkerd através de ClusterIssuer selfSigned, Issuer e Certificate.
  - :heavy_check_mark: Como o ClusterIssuer é selfSigned não precisa de uma CA (Autoridade Certificadora) para os certificados serem criados.

## Identity & Access Management
- OAuth2
  - :heavy_check_mark: Integrar autenticação com github 

- Pomerium

## Kubernetes
- kube-bench
  - :hourglass_flowing_sand: Estudar e entender CIS Kubernetes Benchmark.

- Kubescape

- Trivy

- Falco
  - :hourglass_flowing_sand: Com módulo Kernel com versão acima de 5.x.x não funciona, deu ruim pra testar usando o Kind. Tentar com módulo eBPF.

## Secrets
- Sealed Secrets
  - :heavy_check_mark: Habilitar com certificado próprio para ser único em todas vezes que sobe o cluster local.

- Vault
  - :hourglass_flowing_sand: Habilitar modo dev para testes iniciais.

- External Secrets Operator
  - :hourglass_flowing_sand: Integrar com Vault para buscar credenciais.

