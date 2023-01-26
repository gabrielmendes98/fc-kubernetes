# Kubernetes

Repositório criado para praticar conceitos do Kubernetes. Estou usando o Kind, para não precisar usar um cloud provider e evitar gastos.

### Criando cluster

`kind create cluster --config=k8s/kind.yaml --name=fullcycle`

### Teste de carga

`kubectl run -it fortio --rm --image=fortio/fortio -- load -qps 800 -t 120s -c 70 "http://goserver-service/healthz"`
