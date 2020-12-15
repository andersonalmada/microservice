# Train Ticket：A Benchmark Microservice System 

The project is a train ticket booking system based on microservice architecture which contains 41 microservices. The programming languages and frameworks it used are as below. 
- Article: 
https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8449560

```
git clone --depth=1 https://github.com/FudanSELab/train-ticket.git

cd train-ticket/

cd deployment/kubernetes-manifests/quickstart-k8s

# Deploy the databases
kubectl apply -f quickstart-ts-deployment-part1.yml
# Deploy the services
kubectl apply -f quickstart-ts-deployment-part2.yml
# Deploy the UI Dashboard
kubectl apply -f quickstart-ts-deployment-part3.yml

# Check pods are in a ready state
kubectl get pods

# Visit the Train Ticket web page at http://[Node-IP]:32677.
```
