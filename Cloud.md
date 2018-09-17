
### K8S
* SDN: https://tonybai.com/2017/01/17/understanding-flannel-network-for-kubernetes/
* https://www.kubeflow.org/
* https://ksonnet.io/

K8S Service:
* kubectl get service
* kubectl delete svc <name>

K8S pod:
* kubectl get pods
* kubectl delete pods <pod>

K8S deployments:
* kubectl get deployments
* kubectl delete deployment <name>

K8S Nodes:
* kubectl get nodes
* kubectl delete node <name>

Old School


Apache

* sudo sh -c "echo -n 'sammy:' >> /etc/nginx/.htpasswd"
* sudo sh -c "openssl passwd -apr1 >> /etc/nginx/.htpasswd"


Nginx:

```
server {  
  listen 8888 ssl; 
  server_name server.domain;
  location / {
    proxy_pass http://127.0.0.1:8889;
    # 把 server.domain 指到本地端 8889 port
  }

  ssl_certificate /dir/cert.pem;
  ssl_certificate_key /dir/privkey.pem;
}
```
