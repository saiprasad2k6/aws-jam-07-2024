If you don’t have the CLI configured download and configure it :
http://docs.aws.amazon.com/cli/latest/userguide/installing.html


#### Create VPC:
```console 
aws ec2 create-vpc --cidr-block 10.0.0.0/16
aws ec2 create-tags --resources vpc-d363afab --tags Key=Name,Value=CLI-VPC
```

#### Create a public Subnet:
```console 
aws ec2 create-subnet --vpc-id vpc-d363afab --cidr-block 10.0.1.0/24
aws ec2 create-tags --resources subnet-7314ad17 --tags Key=Name,Value=CLI-Public-Subnet
```
#### Create a private Subnet:
```console 
aws ec2 create-subnet --vpc-id vpc-d363afab --cidr-block 10.0.2.0/24
aws ec2 create-tags --resources subnet-4109b025 --tags Key=Name,Value=CLI-Private-Subnet
```
Create an Internet Gateway:
```console 
aws ec2 create-internet-gateway
aws ec2 create-tags --resources igw-afdd01d6 --tags Key=Name,Value=CLI-Internet-Gateway
```
Attach Internet Gateway:
```console 
aws ec2 attach-internet-gateway --internet-gateway-id igw-5d685a38 --vpc-id vpc-d363afab
```

Allocate Elastic IP:
```console 
aws ec2 allocate-address --domain vpc
```

Create a Nat-gateway and place it in the public Subnet:
```console 
aws ec2 create-nat-gateway --subnet-id subnet-1a2b3c4d --allocation-id eipalloc-37fc1a52
aws ec2 create-tags --resources nat-0e4d97e539eadf232 --tags Key=Name,Value=CLI-Nat-Gateway
```

Create Route Table 1 for public Subnet:
```console 
aws ec2 create-route-table --vpc-id vpc-d363afab 
aws ec2 create-tags --resources rtb-14c3736e --tags Key=Name,Value=CLI-PUBLIC_RT
```

Create Route Table 2 for private Subnet:

```console 
aws ec2 create-route-table --vpc-id vpc-d363afab 
aws ec2 create-tags --resources rtb-cbc070b1 --tags Key=Name,Value=CLI-PRIVATE_RT 
```

Create a route to the internet in Route Table 1:
```console 
aws ec2 create-route --route-table-id rtb-14c3736e --destination-cidr-block 0.0.0.0/0 --gateway-id igw-afdd01d6
```

Create a route to the internet in Route Table 2 via Nat:
```console 
aws ec2 create-route --route-table-id rtb-cbc070b1 --destination-cidr-block 0.0.0.0/0 -- gateway-id nat-0e4d97e539eadf232
```

Associate Route Table 1 to PublicSubnet :
```console 
aws ec2 associate-route-table --route-table-id rtb-14c3736e --subnet-id subnet-7314ad17
```

Associate Route Table 2 to PrivateSubnet:
```console 
aws ec2 associate-route-table --route-table-id rtb-1245623e --subnet-id subnet-234567as
```

