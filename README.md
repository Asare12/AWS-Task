# AWS-Task

## How to create an ec2 instance and deploying the node app
### First Step
- Navigate to EC2 on AWS services

### Second Step
- Navigate and click launch instance

### Third Step
- Choose an Amazon Machine Image(AMI) of your choice
- In my case I choose Ubuntu Server 16.04 LTS (HVM), SSD Volume Type

### Fourth Step
- We then choose the the instance type
- In my case I choose t2.micro

### Fifth Step
- We then fill in the configure instance details
- Configure the instance to suit your requirements. You can launch multiple instances from the same AMI, request Spot instances to take advantage of the lower pricing, assign an access management role to the instance

### Sixth Step
- We then add storage
- You may add tags if you wish

### Seventh Step
- We then configure security group
- You may create one or select one if some exists
- Then you can add a few rules for your instance

### Eigth Step
- We then launch the instance
- You should see your instance on the list
- If you click on your instanceID then connect

### Ninth Step
- Next we want to connect our instance using ssh
- So we need to navigate to ssh tab bar
