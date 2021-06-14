# AWS-Task
# Cloud-computing-and-AWS
- ## [Intro presentation to cloud computing and AWS](https://docs.google.com/presentation/d/1mCpHtCIQjaBd_lCSvReo3g7xFn86ZkB96lQiQ9dSDeI/edit#slide=id.p)

## How to create an ec2 instance and deploying the node app
- Navigate to EC2 on AWS services
- Navigate and click launch instance
- Choose an Amazon Machine Image(AMI) of your choice
- In my case I choose Ubuntu Server 16.04 LTS (HVM), SSD Volume Type
- We then choose the the instance type
- In my case I choose t2.micro
- We then fill in the configure instance details
- Configure the instance to suit your requirements. You can launch multiple instances from the same AMI, request Spot instances to take advantage of the lower pricing, assign an access management role to the instance
- We then add storage
- You may add tags if you wish
- We then configure security group
- You may create one or select one if some exists
- Then you can add a few rules for your instance
- We then launch the instance

## Deploy the node App
- Open AWS and a local terminal
- You should see your instance on the list
- If you click on your instanceID then connect
- Under the SSH client column you will find informations on how to connect via SSH
- Do chmod 400 devop_bootcamp.pem (this is the key file)
- Now ssh into your VM using the ssh command provided in AWS: ssh -i "devop_bootcamp.pem" user@awsVirtualMachineLink.com
- After you managed to ssh into your VM do the following:
  - sudo apt-get update -y
  - sudo apt-get upgrade -y
  - sudo apt-get install nginx
- Now you need to exit from your VM
- Do the following
  - scp -i ~/.ssh/devop_bootcamp.pem /home/user/app user@vmLink.com:/home/ubuntu/
- Go inside /home/ubuntu/app
- run node app.js
- access yourIP:3000 in the browser

## Seting porvision.sh file in `/home/ubuntu/app`
```
#!/bin/bash
sudo apt-get update -y

sudo apt-get upgrade -y

sudo  apt-get install nginx -y

sudo systemctl enable nginx

sudo apt-get install nodejs -y

sudo apt-get install npm-y

sudo apt-get install python-software-properties

curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash

sudo apt-get install nodejs -y

sudo npm install pm2 -g

npm install

cd app 
```

## Reverse proxy
If you wish to reverse proxy you must change your default file in /etc/nginx/sites-available/default and replace with this:
```
server {
        listen 80;
        server_name _;
        location / {
                proxy_pass http://(public ip):3000;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection 'upgrade';
                proxy_set_header Host $host;
                proxy_cache_bypass $http_upgrade;
        }
}
```
