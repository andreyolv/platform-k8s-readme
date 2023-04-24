# platform-k8s-readme

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


