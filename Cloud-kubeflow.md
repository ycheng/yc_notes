
Access minio-service from notebook:
* ./mc config host add sminio http://minio-service.kubeflow:9000  minio minio123
* ref: https://docs.min.io/docs/minio-client-quickstart-guide.html

Notebook engine
* kubeflow_jupyter-web-app-deployment

Resource or links
* kubeflow
* fairing related:
  * https://github.com/kubeflow/fairing/tree/master/examples/prediction
  * https://github.com/kubeflow/fairing/issues/369