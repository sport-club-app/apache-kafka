#####

link:

https://learnk8s.io/kafka-ha-kubernetes

claimRef:
    namespace: kafka
    name: kafka-pvc-kafka-0 (O NOME DEVE SER POR CONVENÇÃO SEGUINDO NOME ${nome volumeMounts}-${nome statefulset})



kubectl run kafka-client --rm -ti --image bitnami/kafka:3.1.0 -- bash

producer

kafka-console-producer.sh \
  --topic vendas \
  --request-required-acks all \
  --bootstrap-server kafka-svc:9092


consumer

kafka-console-consumer.sh \
  --topic vendas \
  --from-beginning \
  --bootstrap-server kafka-svc:9092


description

kafka-topics.sh --describe \
  --topic vendas \
  --bootstrap-server kafka-svc:9092



DRENAR

kubectl drain node2 \
  --delete-emptydir-data \
  --force \
  --ignore-daemonsets 
  node/node2 cordoned 
  evicting pod kafka/kafka-0 
  pod/kafka-0 evicted 
  node/node2 evicted


kubectl uncordon node2 node/node2 uncordoned



  ssh -o StrictHostKeyChecking=no vagrant@192.168.50.23 sudo rm -rf kafka


  sudo kubectl config set-context --current --namespace=kafka

 zookeeper-shell.sh zookeeper-svc get /brokers/ids/0
