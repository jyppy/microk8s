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

