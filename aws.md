# AWS cli examples

### Show EC2 instances with a Name tag equal to eks-node
```
aws ec2 describe-instances \
   --filters "Name=tag:Name,Values=eks-node" \
   --query 'Reservations[*].Instances[*].[PrivateIpAddress, InstanceId]' \
   --output text
```

### Show EC2 instance attached to a particular Security Group
```
aws ec2 describe-instances \
   --filters "Name=instance.group-id,Values=sg-xxxxxxxx" \
   --query 'Reservations[*].Instances[*].[PrivateIpAddress, InstanceId, Tags[?Key==`Name`]]' \
   --output text
```

### Get spot fleets valid ValidUntil
```
aws ec2 describe-spot-fleet-requests \
   --query 'SpotFleetRequestConfigs[*].[SpotFleetRequestId, SpotFleetRequestConfig.ValidUntil]'
```
