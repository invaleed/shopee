### Kubernetes installation 
```sh
Please follow [howto-create-kubernetes-cluster-aws-kops.txt](https://github.com/invaleed/howto-create-kubernetes-cluster-aws-kops.txt)
```

### Configure AWS Key
```sh
$ aws configure
AWS Access Key ID []: __input_your_access_key__
AWS Secret Access Key []: __input_your_secret_access_key__
Default region name []: ap-southeast-1
Default output format [None]: json
```
### Deploy Wordpress to kubernetes
```sh
$ git clone https://github.com/invaleed/shopee.git
$ cd shopee
$ kubectl create secret generic mysql-pass --from-literal=password=YOUR-PASSWORD
$ kubectl create -f mysql-deployment.yaml
$ kubectl create -f wordpress-deployment.yaml
```
### Access to Wordpress Installation
```sh
$ kubectl describe svc ingress-nginx -n ingress-nginx |grep LoadBalancer|awk '{print $3};'
$ curl http://EXTERNAL_IP
```
### Increase & Decrease Capacity (Scaling)
```sh
$ kubectl scale deployment wordpress --replicas=3
$ kubectl scale deployment wordpress --replicas=1
```
