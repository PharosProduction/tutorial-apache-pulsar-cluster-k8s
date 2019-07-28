# Tutorial on How to Deploy Apache Pulsar Cluster in Kubernetes.

## You can find it in our Medium publication
[Pharos Production Medium Article](https://medium.com/pharos-production).

Also you're warmely welcome to say hello to us
[Pharos Production - Blockchain and FinTech Software Development](https://pharosproduction.com)


## Short step-by-step instruction
### ZooKeeper
You must deploy ZooKeeper as the first Pulsar component, as it is a dependency for the others.

$ kubectl apply -f zookeeper_micro.yaml

### Initialize cluster metadata
Once ZooKeeper is running, you need to initialize the metadata for the Pulsar cluster in ZooKeeper. This includes system metadata for BookKeeper and Pulsar more broadly. There is a Kubernetes job in the cluster-metadata.yaml file that you only need to run once:

$ kubectl apply -f cluster-metadata.yaml

### Deploy the rest of the components

Once cluster metadata has been successfully initialized, you can then deploy the bookies, brokers and the Pulsar dashboard.

$ kubectl apply -f bookie.yaml

$ kubectl apply -f broker.yaml

$ kubectl apply -f pulsar-dashboard.yaml
