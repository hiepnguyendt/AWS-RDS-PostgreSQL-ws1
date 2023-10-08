---
title : "Create EC2 instance for app server"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 2.5. </b> "
---


#### To create an EC2 instance for an app server, follow these steps:

1. Open the **Amazon EC2** [console](https://console.aws.amazon.com/ec2/).
2. Click **Launch Instance**.

![Create EC2 instance](/images/preparation/ec2/1.png)

3. Choose an **AMI**. For an app server, you can choose a **Linux AMI**, such as **Amazon Linux 2**.
4. Choose an **instance type**. The instance type that you choose will depend on the requirements of your app server. For example, if you are running a high-traffic website, you will need a larger instance type with more CPU and memory.

![Create EC2 instance](/images/preparation/ec2/2.png)

![Create EC2 instance](/images/preparation/ec2/4.png)

5. For **Key Pair**,choose your keypair you have created or click **Create new key pair** 

![Create EC2 instance](/images/preparation/ec2/5.png)
Configure the instance details. This includes things like the number of instances to launch, the network configuration, and the storage configuration.

7.  For **Network settings**
- Choose **VPC** which contains EC2 app server
- Choose **Subnet**
- **Enable** Auto-assign public IP
- Add a **security group** for EC2 app server that you have created easier step . *A security group is a firewall that controls incoming and outgoing traffic to your instance.* 

![Create EC2 instance](/images/preparation/ec2/6.png)

8. **Review** and **launch** the instance

![Create 7C2 instance](/images/preparation/ec2/7.png)

*Once the instance is launched, you can connect to it using an SSH client, such as MobaXterm or Putty. Once you are connected, you can install your app server and deploy your application.*