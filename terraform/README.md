


#### 01- Generate a ssh pair key

```
$ ssh-keygen -t rsa -f ec2_rsa_key -C "this my private key to access ec2"
```

#### 02- copy the public key ec2_rsa_key.pub to the terraform Folder


#### 03- open the file and change the following with your aws access key and secret key: 
```
region     = "eu-south-1"
access_key = "CHANGE_ME"
secret_key = "CHANGE_ME"
```

#### 04- change the ami key with your value, check the [Ami references](#AMI-REFERENCES) to choose your image: 
```
ami = "CHANGE_ME"
```

#### 05- initialize terraform working directory bu runing the below command: 
```
$ terraform init
```


#### 06- Validate and apply to create your aws EC2 instance: 
```
$ terraform validate
$ terraform apply
```

The output should be something like this:
```
Apply complete! Resources: 10 added, 0 changed, 0 destroyed.

Outputs:

public_dns = ec2-*-*-*-*.eu-south-1.compute.amazonaws.com
public_ip = XXX.XXX.XXX.XXX
```




### AMI-REFERENCES

| os               | AMI                    |
| ---------------- | ---------------------- |
| Ubuntu 16.04 LTS | ami-0ae82b98c54a93226  |
| Ubuntu 18.04 LTS | ami-0748c300929be9a20  |
| Ubuntu 20.04 LTS | ami-0b74d52f736d963d1  |
| Rhel 8           | ami-05f5fb99d4803eb99  |
| Rhel 7           | ami-                   |
| centOS 8         | ami-                   |
| centOS 7         | ami-                   |
