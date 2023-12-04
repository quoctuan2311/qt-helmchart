# helmchart

**Helmchart Install Guilde**

*Install Helm (Centos)*
  - wget https://get.helm.sh/helm-v3.3.2-linux-amd64.tar.gz
  - tar -zxvf helm-v3.3.2-linux-amd64.tar.gz
  - sudo mv linux-amd64/helm /usr/local/bin/helm

*Create Helm Chart*
  - helm create qt-chart


*Index Helm Repo*
  - helm package qt-chart
  - mkdir helm-repo
  - mv qt-chart-0.1.0.tgz helm-repo/
  - helm repo index helm-repo --url https://helm-repo.qt.com.vn
  - upload file .tgz and index.yaml to bucket s3


*How To Use*
  - helm repo add helm-repo https://helm-repo.qt.com.vn
  - touch values.yml
  - helm template <service-name> helm-repo/qt-chart -f values.yaml




