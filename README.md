# AWS_RstudioserverInstall
Steps to install rstudio server on AWS Linux, including script on EC2 launch

##Installing Rstudio server on AWS Linux
Requirements: allow custom TCP on Port 8787 of the relevant security group

------------------------
MANUAL INSTALLATION

On Ubuntu
SSH into EC2 instance

Step 1:
$ sudo yum update -y

Step 2:
[DEPRECATED] sudo yum install R
$ sudo amazon-linux-extras install R3.4

$wget https://download2.rstudio.org/server/centos6/x86_64/rstudio-server-rhel-1.2.5019-x86_64.rpm
$ sudo yum install rstudio-server-rhel-1.2.5019-x86_64.rpm

[checking installation worked]
$ sudo rstudio-server verify-installation

$ sudo useradd testuser
$ echo testuser:testPassword | sudo chpasswd

Connecting to the server from the browser
<publicIP>:8787
user: testUser
password: testPassword

-------------------------
SCRIPT to be copied for EC2 instance launch
#!/bin/bash
sudo yum update -y
sudo amazon-linux-extras install R3.4 -y
wget https://download2.rstudio.org/server/centos6/x86_64/rstudio-server-rhel-1.2.5019-x86_64.rpm
sudo yum install rstudio-server-rhel-1.2.5019-x86_64.rpm -y
sudo useradd testUser
echo testUser:testPassword | sudo chpasswd

-------------------------

