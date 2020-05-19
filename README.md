# assignment

This ansible playbooks will:
<ul>
  <li>Install Epel Release Repository (RHEL/CENTOS)</li>
  <li>Install Lamp Stack(Install && secure mariadb, Install && hardening Httpd, install php from remi repository)</li>
  <li>Install Wordpress</li>
  <li>Configure Your VirtualHost</li> 
  </ul>
 
 
# Requirements
  Ubuntu : 16.04 LTS / 18.04 LTS / 20.04 LTS
  Redhat/CentOS: 7 / 8


#### 01- modify the following variables in the file inventory/group_vars/all.yml by yours to gain access to the aws instance(s).                                                                    
```
ansible_user: ubuntu
ansible_ssh_private_key_file: {PATH}/ec2_rsa.pub
```

- The ```ansible_ssh_private_key_file``` should the the private key that been created int the first step, check out here [here](https://github.com/faudeltn/assignment/tree/master/terraform#01--generate-a-ssh-pair-key)


- The ```ansible_user``` could be ```ec2-user``` if you choose Redhat/ CentOS ami or ```ubuntu``` if you choose the Ubuntu ami.

#### 02- Open the inventory/main.yml file and modify the ```YOUR_PUBLIC_DNS_INSTANCE``` and ```YOUR_PUBLIC_IP_INSTANCE``` with the output of your terraform apply command result:
```
---
all:
  hosts:
    YOUR_PUBLIC_DNS_INSTANCE:
      ansible_host: YOUR_PUBLIC_IP_INSTANCE
```

#### 03- Modify the enviroment variables as you prefer in the file /vars/main.yml:

<u>
  <li><strong>mariadb_root_password</strong>: The MariaDB root password, change it with your own password.</li>
  <li><strong>mariadb_version</strong>:The version of MariaDB to be installed.</li>
  <li><strong>mariadb_packages</strong>: Install the required packages; MariaDB-server, MySQL-python</li>
  <li><strong>remi_repo_name</strong>: the Remi repository name, could be remi-php74, remi-php72 ... </li>
  <li><strong>mysql_db</strong>: the name of the wordpress database to be created</li>
  <li><strong>mysql_user</strong>: the username of the wordpress database</li>
  <li><strong>mysql_password</strong>: the password of the wordpress user</li>
  <li><strong>http_host</strong>: the domain name of your website</li>
  <li><strong>http_conf</strong>: the virtual Host config file of your domain</li>
  <li><strong>http_port</strong>: the protocol to use, for the moment it's just compatible with the port 80 not 443, will be extended in the next version of this playbook</li>
</u>

#### 04 - To run this playbook use the following command

```
ansible-playbook -i inventory/main.yml -e @vars/main.yml lamp-install.yml
```
