# Backup a Crunchy Postgres database with Kasten
In this project, I demonstrate on how to backup a crunchy postgres database with Kasten K10

### Why Crunchy Postgres?

As organizations deploy more complex workloads, there is a growing trend of operators based data services being natively deployed into kuberenets clusters. For instance with PGO, the Postgres Operator from Crunchy Data, offers a solution that automatically manages the PostgreSQL clusters on kubernetes. Deploying a production grade Postgres cluster with high availability and enterprise ready features becomes much easier with the operator approach. Crunchy Data Postgres Operator (PGO), natively integrates with open source pgBackrest tool to backup and restore PostgreSQL data

### Why Kasten K10?

often times, 


Kasten K10, is a data protection solution that was purpose-built for Kubernetes. It provides enterprise operations teams with an easy-to-use, scalable, and secure system for backup, restore, disaster recovery and the mobility of Kubernetes applications.

Create the namespace and install pgo
```
kubectl create namespace postgres-operator
kubectl config set-context --current --namespace postgres-operator


# Install PGO and create the cluster

To install PGO itself in cluster-wide mode, apply the kustomization file in the default folder:

kubectl apply --server-side -k /opt/postgres-operator/postgres-operator-examples/kustomize/install/default

Create a Postgres Cluster

kubectl apply -k /opt/postgres-operator/postgres-operator-examples/kustomize/postgres
watch kubectl get pods -n postgres-operator
