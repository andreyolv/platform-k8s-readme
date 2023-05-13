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

# Data
## SQL Databases
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/3bd57497-3fc2-4c35-ab4f-b0f25c1def3d)
- MySQL
- PostgreSQL

## NoSQL Databases
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/93dcb58b-15b3-4e9c-aee6-c560c6673e21)
- MongoDB
- Redis
- Cassandra
- Neo4j
- YugabyteDB

## Orchestration
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/123bca7d-9907-431a-9586-724524f673f8)
- Airflow
- Nifi
- Prefect
- Dagster

## Processing
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/2d784fae-51e9-4342-8f74-963f9deb2ee6)
- Spark
- Dbt (Data Build Tool)
- ksqldb
- Flink

## Lakehouse
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/cb87acab-2b99-49e3-8ff4-5229acb7cf62)
- Delta
- Iceberg

## Query Engine
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/856c32a2-95f7-4188-9338-7b8da510c686)
- Trino
- Dremio

## Machine Learning
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/eb648683-bca9-4c52-a6f5-8e1d23aef136)
- Mlflow
- Kubeflow

## Lake Versioning
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/fbebb26c-b41b-4a4e-849a-62867808e796)
- lakeFS
- Nessie

## Viz
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/958f25f1-109b-4c70-b507-0882fbe5fe1a)
- Superset
- Metabase

## Integration
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/2962fdb0-c4ec-45f4-9923-365e92822b11)
- Airbyte
- SeaTunnel

## OLAP Realtime
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/700afec8-2261-4aef-af04-0b6f0993df74)
- Pinot
- Clickhouse

## Catalog
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/fdbe5f94-eb18-4128-8dac-4884c2ba494c)
- Datahub
- OpenMetadata

## Quality
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/0d2f6d3b-7e30-40e2-933b-e0248df51fd6)
- Great Expectations
- SODA

## Lineage
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/52c5cdf4-0428-4520-acb4-ea7232c62744)
- OpenLineage
- Marquez

## Change Data Capture
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/e6b55ee2-497f-46bf-b805-8f7b9ed5aa0e)
- Debezium

---------------------------------------------------------------------
# DevOps
## Container Images
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/7f81faf1-5f6a-4544-9e02-eaca5e5367d1)
- Docker
- Kaniko
Lê um Dockerfile do meu repositório privado do github. builda a imagem dentro do kubernetes e envia para minha conta do Dockerhub
- Harbor

## Infrastructure as Code
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/8bce6cab-065d-4c29-b5d2-85542dc7c17e)
- Terraform
- Crossplane

## Temaplate Configuration
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/db8cfec4-4bc5-4ad4-841e-b124970dcbc9)
- Helm
- Kustomize

## Service Mesh
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/6ce70084-bdcf-4523-8b3f-89d50de891e7)
- Linkerd
Gera certificados do tipo selfsigned pelo Cert-manager, 
Implementa control plane, linkerd-viz, linkerd-multicluster
- Cilium

## CI/CD
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/3b505a5d-cb1b-4599-a5f4-510dcf5cabf0)
- Github Actions
- Tekton
- Jenkins

## GitOps
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/ae113bd7-7808-4cfe-9982-1af5030d48b6)
- Flux
- ArgoCD

## API Gateway
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/a199ebf6-c080-4f30-9c58-faa0b85fa315)
- Kong
- APISIX
- Emissary Ingress

## Reverse Proxy
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/2f77432d-ecce-4290-a216-a06b753ef4b7)
- Nginx
- Traefik

## Compliance
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/43d231e1-efc6-4bdb-91fd-5aa4d0b29170)
- Kyverno
Contém UI policy-reporter
- Open Policy Agent
- Datree
- SonarQube

## Version Control
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/28870f3b-9423-4db0-b833-a7045d2ba9cd)
- Git
- Github

## Progressive Delivery
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/872ba461-5485-4aa9-8040-ee9881964bab)
- Flagger
- Keptn

## Cost
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/791c76af-04ce-4835-8769-930801c83487)
- OpenCost
- Infracost

## Cluster Management
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/e49aaec1-5bf9-402e-9533-a09fc941289f)
- Portainer
- Rancher
- Kubesphere

## Storage
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/43b10216-9121-4739-99aa-969ee3b2b104)
- MinIO
Integrado com spark no jupyter notebook
Integrado com velero
Integrado com delta / lakehouse
Integrado para logs do spark history server
- Velero
- Longhorn

## Developer Portals
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/dcb1fa4a-c020-412a-bdcc-c51f99f57e49)
- Backstage

## Configuration
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/26e97dbc-98f4-4a00-8c73-4dd6c6d59837)
- Ansible

## Troubleshooting
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/8a3da6bf-5c06-4e09-b4a2-59b9b445a36c)
- Komodor

---------------------------------------------------------------------
# Observability
## Abastraction Layer
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/7f90ee0a-9b61-4f0b-83c3-fbfe45d894b2)
- OpenTelemetry

## Collector
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/b89da536-51a9-4be4-9f4c-a606676adc85)
- fluent / fluentD

## Metrics
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/4de09b5e-05b5-486b-985d-a130024a81bb)
- Prometheus

## Logs
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/6034d0f7-ff2f-4540-8501-a60150adace6)
- ElasticSearch
- Loki

## Dashboards
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/35583e47-c108-462f-b3b0-53ad5e90dc79)
- Grafana
- Kibana

## Alerts
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/71f5eacc-d072-4bbf-a3e2-f240590732ae)
- Robusta

## Tracing
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/3a9a16a0-eeff-4158-94e3-ca4b97723587)
- Jaeger
- Zipkin

## Chaos Engineering
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/0dda331d-9085-4ac8-a4b7-8259e6ba2427)
- ChaosMesh
- Litmus

---------------------------------------------------------------------
# Security
## Identity & Access Management
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/e7dfb5ef-b038-4199-852a-e768d055568b)
- OAuth2
- Keycloack
- Pomerium
- Teleport

## Kubernetes
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/55951df8-2ff3-4a50-a419-b136b795bf22)
- Kubescape
- Falco
- kube-bench
- trivy

## Certificates
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/4c20c672-c231-4cc6-a038-a78bec36c901)
- cert-manager
Integrado com o Linkerd, gerando ClusterIssuer selfsigned. Certificate e Issuer.
Como é selfsigned não precisa de uma CA (Autoridade Certificadora)

## Secrets
![image](https://github.com/andreyolv/platform-k8s-readme/assets/49295662/6a5f135a-63c1-41f6-bdd0-20fc79ecd6e2)
- Sealed Secrets
- Vault
- External Secrets Operator

