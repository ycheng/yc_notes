
# Locale plugin
* So you can see English no matter what's your browser's preferences.

# K8S Plugin

* Plugin: https://plugins.jenkins.io/kubernetes

How to config:

* Step 1: connection to k8s
  * https://illya-chekrygin.com/2017/08/26/configuring-certificates-for-jenkins-kubernetes-plugin-0-12/
  * Key Points: value from ~/.kube/config
  * value of certificate-authority-data: echo LSuperLongBase64EncodedString== | base64 -d > ca.crt
  * put it in "Kubernetes server certificate"
  * Credentials, for user name / password, just paste the value

* Step 2: k8s connect to Jenkins master
  * https://medium.com/vivid-seats-engineering/how-to-kubernetes-pods-as-jenkins-build-agents-a726d3886861
  * Key Points:
  * Jenkins URL to http://<your_ip_address>:8080
  * “Configure Global Security” => “Agents TCP port for inbound agents” => Fixed a port like 8081, and change the URL to http://<your_ip_address>:8081 so that it works.
