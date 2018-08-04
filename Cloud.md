
* K8S
  * SDN: https://tonybai.com/2017/01/17/understanding-flannel-network-for-kubernetes/
  * https://www.kubeflow.org/
  * https://ksonnet.io/



Old School


Nginx:
'''
server {  
  listen 8888 ssl; 
  server_name server.domain;
  location / {
    proxy_pass http://127.0.0.1:8889;
    # 把 www.example.com 指到本地端 8889 port
  }

  ssl_certificate /dir/cert.pem;
  ssl_certificate_key /dir/privkey.pem;
}
'''