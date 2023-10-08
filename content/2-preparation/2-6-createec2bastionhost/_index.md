---
title : "Create bastion host EC2 instance "
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 2.6. </b> "
---


{{% notice note %}}
We will connect to a PostgreSQL RDS instance using pgAdmin 4 through a jump host EC2 bastion host
{{% /notice %}}

#### To create an EC2 instance for bastion host , follow these steps:

1. Open the **Amazon EC2** [console](https://console.aws.amazon.com/ec2/).
2. Click **Launch Instance**.

![Create bastion host](/images/preparation/ec2/1.png)
3. **Name** for EC2 bastion host

![Create bastion host](/images/preparation/bastionhost/ec2bastion.png)
3. Choose an **AMI**. For an app server, you can choose a **Linux AMI**, such as **Amazon Linux 2**.

![Create bastion host](/images/preparation/bastionhost/ec2bastion1.png)

4. Choose an **instance type**. The instance type that you choose will depend on the requirements of your app server. For example, if you are running a high-traffic website, you will need a larger instance type with more CPU and memory.

![Create bastion host](/images/preparation/bastionhost/ec2bastion2.png)

5. For **Key Pair**,choose your keypair you have created or click **Create new key pair** 


![Create bastion host](/images/preparation/bastionhost/ec2bastion3.png)

Configure the instance details. This includes things like the number of instances to launch, the network configuration, and the storage configuration.

7.  For **Network settings**
- Choose **VPC** which contains EC2 app server
- Choose **Subnet**
- **Enable** Auto-assign public IP
- Add a **security group** for EC2 app server that you have created easier step . *A security group is a firewall that controls incoming and outgoing traffic to your instance.* 

![Create bastion host](/images/preparation/bastionhost/ec2bastion4.png)

8. **Review** and **launch** the instance

![Create bastion host](/images/preparation/bastionhost/ec2bastion5.png)

