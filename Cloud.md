### MicroK8s
* docker in microk8s: also have nvidia runtime support ! yes ! however, -p port1:port2 is not supported.
* microk8s.docker create -it --name tf --runtime nvidia tf/tf:version /bin/bash
* https://github.com/canonical-labs/kaggle-kubeflow-tutorial works, with the following
 * cpu set to "1.0", mem set something smaller, I begin with "300Mi"


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
* kubectl get rs # replica set
* kubectl get pods --show-labels
* kubectl rollout status deployment/deployment-name
* kubectl set image deployment/deployment-name k8s-demo=k8s-demo:2 # update app version
* kubectl edit deployment/deployment-name
* kubectl rollout status deployment/deployment-name
* kubectl rollout history deployment/deployment-name
* kubectl rollout undo deployment/deployment-name
* kubectl rollout undo deployment/deployment-name --to-revision=n

K8S Nodes:
* kubectl get nodes
* kubectl delete node <name>

K8S Replication Controller:
* kubectl get rc
* kubectl scale --replicas=n rc/rc-name
* kubectl scale --replicas=n -f pod_file_with_rc.yml
* kubectl delete rc/rc-name

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
