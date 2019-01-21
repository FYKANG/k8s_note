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
