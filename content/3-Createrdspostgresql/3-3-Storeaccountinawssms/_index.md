---
title : "Password management with Amazon RDS and AWS Secrets Manager"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 3.3. </b> "
---

 **Secrets Manager** enables you to replace hardcoded credentials in your code, including passwords, with an API call to Secrets Manager to retrieve the secret programmatically. This helps ensure the secret can't be compromised by someone examining your code, because the secret no longer exists in the code.

 1.Open [AWS Management console](https://aws.amazon.com/premiumsupport/knowledge-center/sign-in-console/),
 - Find **Secrets Manager**
 - Select **Secrets Manager**

 ![sms](/images/3/3-3/16.png)

 2.Click **Store a new secret** to start the configuration process.

 ![sms](/images/3/3-3/17.png)

 3.In the Select secret type section, 
 - Choose **Credentials for RDS database**
 - Input the **User name** (should be masteruser) and **Password** that you provided when you created the DB cluster previously. 
 ![sms](/images/3/3-3/18.1.png)

 - Next, in the Select which RDS database this secret will access section, choose the **DB instance identifier** you assigned to your instance (e.g. rdspg-fcj-labs). Click Next.

 ![sms](/images/3/3-3/19.png)

 4.Name the secret ``secretPostgresqlMasterUser`` and provide a relevant description for the secret, then click Next.

 ![sms](/images/3/3-3/20.png)

  {{% notice note%}}
 Be sure to use the exact name (case-sensitive) of secretPostgresqlMasterUser to avoid having to edit some of the lab scripts later.
 {{% /notice %}}

 5.Finally, in the **Configure automatic rotation** section, leave the option of Disable automatic rotation selected. In a production environment you will want to use database credentials that rotate automatically for additional security. Click Next.
 ![sms](/images/3/3-3/21.png)

 6.In the **Review** section you have the ability to check the configuration parameters for your secret, before it gets created. Additionally, you can retrieve sample code in popular programming languages, so you can easily retrieve secrets into your application. Click **Store** at the bottom of the screen.

 ![sms](/images/3/3-3/22.png)

 