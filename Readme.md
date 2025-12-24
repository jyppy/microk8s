Sample CloudFormation template used to create a singlenode microk8 cluster on an EC2 instance

Using the following command, a stack can be created

```
export NAME=yourname
aws cloudformation deploy \
--template-file microk8s-base.yaml \
--stack-name $NAME \
--region ap-southeast-2 \
--parameter-overrides ClusterName=$NAME FQDN=$NAME.apac.venafidemo.com
```
the AllowFromEverywhere tag must be set to "yes" - with quotes or CF will chsnge it to TRUE and the secGroup will not be properly tagged
