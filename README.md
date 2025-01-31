# AWS CloudFormation: Multi-Server Deployment 🚀

# Overview
This repository contains an AWS CloudFormation YAML template that automates the deployment of five web servers using EC2 instances. Each server is configured with Ubuntu or Amazon Linux, installs Apache (httpd) or Nginx, and serves a pre-configured static website from free-css.com.
# Features

✅ Infrastructure as Code (IaC) using AWS CloudFormation

✅ Automated EC2 provisioning with different OS & web servers

✅ Pre-installed Apache (httpd) & Nginx for hosting static websites

✅ Custom Security Group allowing SSH & HTTP access

✅ UserData for automatic package installation & web content setup

# Architecture Diagram
📌 Deployed Resources:

5 EC2 Instances (Ubuntu & Amazon Linux)

Security Groups (Allowing SSH & HTTP access)

Subnet Configuration

``` yaml
AWSTemplateFormatVersion: 2010-09-09
Resources:
  server1:
    Type: 'AWS::EC2::Instance'
    Properties:
      ImageId: ami-09a9858973b288bdd
      InstanceType: t3.micro
      KeyName: stockholm-linux-keypair
      SecurityGroupIds:
      - sg-0e11ab30c5c9f59d1
      SubnetId: subnet-0ddd7b6b3a5f0158a
      UserData:
        Fn::Base64: |
          #!/bin/bash -xe
          sudo apt-get update -y
          sudo apt-get install nginx wget unzip -y
          sudo systemctl start nginx
          sudo systemctl enable nginx
          sudo wget https://www.free-css.com/assets/files/free-css-templates/download/page291/gamepad.zip
          sudo unzip gamepad.zip
          sudo cp -rvf  html/* /var/www/html/
          sudo cp -rvf  html/* /usr/share/nginx/html/
      Tags:
      - Key: Name
        Value: Ubuntu-Webserver-1
  server2:
    Type: 'AWS::EC2::Instance'
    Properties:
      ImageId: ami-09a9858973b288bdd
      InstanceType: t3.micro
      KeyName: stockholm-linux-keypair
      SecurityGroupIds:
      - sg-0e11ab30c5c9f59d1
      SubnetId: subnet-0ddd7b6b3a5f0158a
      UserData:
        Fn::Base64: |
          #!/bin/bash -xe
          sudo apt-get update -y
          sudo apt-get install apache2 wget unzip -y
          sudo systemctl start apache2
          sudo systemctl enable apache2
          sudo wget https://www.free-css.com/assets/files/free-css-templates/download/page292/picstudio.zip
          sudo unzip picstudio.zip
          sudo cp -rvf  picstudio-html/* /var/www/html/
          sudo cp -rvf  picstudio-html/* /usr/share/apache2/html/
      Tags:
      - Key: Name
        Value: ubuntu-server-2
  server3:
    Type: 'AWS::EC2::Instance'
    Properties:
      ImageId: ami-087fba4aa07ebd20f
      InstanceType: t3.micro
      KeyName: stockholm-linux-keypair
      SecurityGroupIds:
      - sg-0e11ab30c5c9f59d1
      SubnetId: subnet-0ddd7b6b3a5f0158a
      UserData:
        Fn::Base64: |
          #!/bin/bash -xe
          yum update -y
          yum install httpd wget unzip -y
          systemctl start httpd
          systemctl enable httpd
          wget https://www.free-css.com/assets/files/free-css-templates/download/page295/finter.zip
          unzip finter.zip
          cp -rvf finter-html/* /var/www/html/
      Tags:
      - Key: Name
        Value: Amazon-Webserver1
  server4:
    Type: 'AWS::EC2::Instance'
    Properties:
      ImageId: ami-087fba4aa07ebd20f
      InstanceType: t3.micro
      KeyName: stockholm-linux-keypair
      SecurityGroupIds:
      - sg-0e11ab30c5c9f59d1
      SubnetId: subnet-0ddd7b6b3a5f0158a
      UserData:
        Fn::Base64: |
          #!/bin/bash -xe
          yum update -y
          yum install httpd wget unzip -y
          systemctl start httpd
          systemctl enable httpd
          wget https://www.free-css.com/assets/files/free-css-templates/download/page291/atlas.zip
          unzip atlas.zip
          cp -rvf /Atlas/*  /var/www/html/
      Tags:
      - Key: Name
        Value: Amazon-Webserver-2
  server5:
    Type: 'AWS::EC2::Instance'
    Properties:
      ImageId: ami-087fba4aa07ebd20f
      InstanceType: t3.micro
      KeyName: stockholm-linux-keypair
      SecurityGroupIds:
      - sg-0e11ab30c5c9f59d1
      SubnetId: subnet-0ddd7b6b3a5f0158a
      UserData:
        Fn::Base64: |
          #!/bin/bash -xe
          yum update -y
          yum install httpd wget unzip -y
          systemctl start httpd
          systemctl enable httpd
          wget https://www.free-css.com/assets/files/free-css-templates/download/page284/dorang.zip
          unzip dorang.zip
          cp -rvf /dorang/public_html/*  /var/www/html/
      Tags:
      - Key: Name
        Value: Amazon-Webserver-3
```

# Connect with Me 🚀
🔹 LinkedIn: https://www.linkedin.com/in/sai-kumar-82ba29265/
