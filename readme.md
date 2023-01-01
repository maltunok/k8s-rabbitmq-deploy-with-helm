# create a namespace in the cluster

kubectl create ns rabbitmq

# add bitnami repo with helm

helm repo add bitnami https://charts.bitnami.com/bitnami

# install rabbitmq with helm and set username and password

helm install rabbitmq \
 --set auth.username=admin,auth.password=Password1,auth.erlangCookie=secretcookie \
 bitnami/rabbitmq \
 -n rabbitmq

# port forward and see the rabbitmq is running

kubectl port-forward --namespace rabbitmq --address 0.0.0.0 svc/rabbitmq 15672:15672
