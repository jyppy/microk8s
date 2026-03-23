Sample CloudFormation template used to create a singlenode microk8s kubernetes Host on an EC2 instance (Ubuntu Linux)

Using the following command, a stack can be created

1/ Create a envVar
```
export NAME=microk8-1
```
2/ Deploy the CF template in your region

```
aws cloudformation deploy \
--template-file microk8s-base.yaml \
--region ap-southeast-2 \
--stack-name $NAME \
--parameter-overrides \
KeyName=my-key \
ClusterName=$NAME \
HostedZoneName=mydomain.test. \
FQDN=$NAME.mydomain.test
```
**Note:** the trailing dot (.) in the HostedZoneName parameter

The AllowFromEverywhere tag must be set to **"yes"** - with quotes or CF will change it to **TRUE** and the securityGroup/EC2Instance will not be properly tagged

3/ Delete stack

```
aws cloudformation delete-stack --stack-name $NAME --region ap-southeast-2
```

# Retrieve the kubeconfig file (Valid for 2 days)

Now that the single node kubernetes node is up and running, the config file will be available for download from a download page provided by the NGINX pod. You will need to authenticate (Basic Auth), to retrieve the config file

[Your assigned Microk8s node](https://FQDN/temp-user.txt)

using this kubeconfig file, you shoud now have access full access to the resources available in that k8s node.

```
kubectl --kubeconfig k8.yaml  get all -A
```


