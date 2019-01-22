# k8s_note
关于k8s的笔记
* kubeadm报错信息
  ```
  name: Invalid value: "vm_40_150_centos": a DNS-1123 subdomain must consist of lower case alphanumeric characters, '-' or '.', and must start and end with an alphanumeric character (e.g. 'example.com', regex use[a-z0-9]([-a-z0-9]*[a-z0-9])?)*')
  ```
  * 解决方法hostname修改
  ```
  hostnamectl set-hostname xxx.xxx.xxx
  ```
* 拉取镜像超时
  * 错误信息
  ```
    [ERROR ImagePull]: failed to pull image k8s.gcr.io/kube-apiserver:v1.13.2: output: Trying to pull repository k8s.gcr.io/kube-apiserver ... 
  Get https://k8s.gcr.io/v1/_ping: dial tcp 108.177.125.82:443: i/o timeout
  , error: exit status 1
    [ERROR ImagePull]: failed to pull image k8s.gcr.io/kube-controller-manager:v1.13.2: output: Trying to pull repository k8s.gcr.io/kube-controller-manager ... 
  Get https://k8s.gcr.io/v1/_ping: dial tcp 108.177.125.82:443: i/o timeout
  , error: exit status 1
    [ERROR ImagePull]: failed to pull image k8s.gcr.io/kube-scheduler:v1.13.2: output: Trying to pull repository k8s.gcr.io/kube-scheduler ... 
  Get https://k8s.gcr.io/v1/_ping: dial tcp 108.177.125.82:443: i/o timeout
  , error: exit status 1
    [ERROR ImagePull]: failed to pull image k8s.gcr.io/kube-proxy:v1.13.2: output: Trying to pull repository k8s.gcr.io/kube-proxy ... 
  Get https://k8s.gcr.io/v1/_ping: dial tcp 108.177.125.82:443: i/o timeout
  , error: exit status 1
    [ERROR ImagePull]: failed to pull image k8s.gcr.io/pause:3.1: output: Trying to pull repository k8s.gcr.io/pause ... 
  Get https://k8s.gcr.io/v1/_ping: dial tcp 108.177.125.82:443: i/o timeout
  , error: exit status 1
    [ERROR ImagePull]: failed to pull image k8s.gcr.io/etcd:3.2.24: output: Trying to pull repository k8s.gcr.io/etcd ... 
  Get https://k8s.gcr.io/v1/_ping: dial tcp 108.177.125.82:443: i/o timeout
  , error: exit status 1
    [ERROR ImagePull]: failed to pull image k8s.gcr.io/coredns:1.2.6: output: Trying to pull repository k8s.gcr.io/coredns ... 
  Get https://k8s.gcr.io/v1/_ping: dial tcp 108.177.125.82:443: i/o timeout
  , error: exit status 1

  ```
  * 处理手动拉取
  ```
  docker pull mirrorgooglecontainers/kube-apiserver:v1.13.2
  docker pull mirrorgooglecontainers/kube-controller-manager:v1.13.2
  docker pull mirrorgooglecontainers/kube-scheduler:v1.13.2
  docker pull mirrorgooglecontainers/kube-proxy:v1.13.2
  docker pull mirrorgooglecontainers/pause:3.1
  docker pull mirrorgooglecontainers/etcd:3.2.24
  docker pull docker.io/willdockerhub/coredns:1.2.6
  docker tag docker.io/mirrorgooglecontainers/kube-controller-manager:v1.13.2 k8s.gcr.io/kube-controller-manager:v1.13.2
  docker tag docker.io/mirrorgooglecontainers/kube-proxy:v1.13.2 k8s.gcr.io/kube-proxy:v1.13.2
  docker tag docker.io/mirrorgooglecontainers/kube-apiserver:v1.13.2 k8s.gcr.io/kube-apiserver:v1.13.2
  docker tag docker.io/mirrorgooglecontainers/kube-scheduler:v1.13.2 k8s.gcr.io/kube-scheduler:v1.13.2
  docker tag docker.io/willdockerhub/coredns:1.2.6 k8s.gcr.io/coredns:1.2.6
  docker tag docker.io/mirrorgooglecontainers/etcd:3.2.24 k8s.gcr.io/etcd:3.2.24
  docker tag docker.io/mirrorgooglecontainers/pause:3.1 k8s.gcr.io/pause:3.1
  ```
