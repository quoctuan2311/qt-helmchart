# Helm Chart

## **Helmchart Install Guilde**

## *Install Helm (Centos)*
```
wget https://get.helm.sh/helm-v3.3.2-linux-amd64.tar.gz
tar -zxvf helm-v3.3.2-linux-amd64.tar.gz
sudo mv linux-amd64/helm /usr/local/bin/helm
```

## *Create Helm Chart*
```
helm create qt-chart
```

## *Index Helm Repo*
```
helm package qt-chart
mkdir helm-repo
mv qt-chart-0.1.0.tgz helm-repo/
helm repo index helm-repo --url https://helm-repo.qt.com.vn
upload file .tgz and index.yaml to bucket s3
```

## *Push Helm Repo to Repository*
```
helm package qt-chart
helm push ./qt-chart-1.3.0.tgz oci://<Repository URL>/qt-chart
```

## *How To Use*
### S3

```
sudo mkdir /opt/qt-chart
aws s3 cp s3://vui-cicd-test/helmchart/qt-chart-1.3.0.tgz ./qt-chart-1.3.0.tgz
sudo mv ./qt-chart-1.3.0.tgz /opt/qt-chart/
```

### Repository

```
helm registry login -u <user> -p <password> https://<Repository URL>/qt-chart
helm upgrade --install <name> oci://<Repository URL>/qt-chart --version 1.3.0
```




