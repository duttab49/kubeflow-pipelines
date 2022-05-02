# kubeflow-pipelines
Work related to Kubeflow pipelines

### Install Kubeflow pipeline SDK 
- pip3 install kfp --upgrade

### How to install Kubeflow pipeline in Docker desktop ?

Run following commands - 
- export PIPELINE_VERSION=1.8.1
- kubectl apply -k "github.com/kubeflow/pipelines/manifests/kustomize/cluster-scoped-resources?ref=$PIPELINE_VERSION"
- kubectl wait --for condition=established --timeout=60s crd/applications.app.k8s.io
- kubectl apply -k "github.com/kubeflow/pipelines/manifests/kustomize/env/platform-agnostic-pns?ref=$PIPELINE_VERSION"
- Wait till all pods in kubeflow namespace are ready.
- kubectl port-forward -n kubeflow svc/ml-pipeline-ui 8080:80

**Verify Kubeflow Pipeline UI is accessible at `http://localhost:80`**.

### Create Kubeflow yaml tar file from python file
- dsl-compile --py add_pipeline.py --output add_pipeline.tar.gz

![image](https://user-images.githubusercontent.com/61991580/166267988-ca303ef1-5b90-4ec5-84ea-bc1f463ec6d4.png)
