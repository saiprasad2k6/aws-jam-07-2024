## EC2 Creation

Running EC2 Instance
```shell
aws ec2 run-instances --image-id ami-6057e21a --instance-type t2.micro --count 3
```

Create a Security Group for Web Access and SSH:
```console 
aws	ec2	create-security-group	--group-name	CLI-WEB-SecurityGroup --description	"Mysecurity	group" --vpc-id vpc-d363afab
aws ec2 create-tags --resources sg-03ca1371 --tags Key=Name,Value=CLI_SECURITY_GROUP
Add Ingress Port 22 and 80:
```

Create Key Pair and copy the key part and write it to a file MyKeyPairCLI.pem :
```console 
aws ec2 create-key-pair --key-name MyKeyPairCLI
```

Change the permissions on that file to restrict access:
```console 
chmod 400 MyKeyPairCLI.pem
```

Launch EC2 Instance In public subnet with Amazon AMI ami-8c1be5f6 :
```console 
aws ec2 run-instances --image-id ami-8c1be5f6 --count 1 --instance-type t2.micro --key- name MyKeyPairCLI --security-group-ids sg-c3ed34b1 --subnet-id subnet-7314ad17 -- associate-public-ip-address
aws ec2 create-tags --resources i-05c8b15394d0905b8 --tags Key=Name,Value=CLI_EC2
```

Describe Instance to get the IP or check the console:
```console 
aws ec2 describe-instances
```

SSH into your web browser:
```console 
ssh ec2-user@34.34.234.4 -i MyKeyPairCLI.pem
```
