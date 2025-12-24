Sample CloudFormation template used to create a singlenode microk8 cluster on an EC2 instance

Using the following command, a stack can be created

1/ Create a envVar
```
export NAME=yourname
```
2/ Deploy the CF template in your region

```
aws cloudformation deploy \
--template-file microk8s-base.yaml \
--region ap-southeast-2 \
--stack-name $NAME \
--parameter-overrides ClusterName=$NAME FQDN=$NAME.apac.venafidemo.com
```
the AllowFromEverywhere tag must be set to "yes" - with quotes or CF will change it to TRUE and the securityGroup/EC2Instance will not be properly tagged
