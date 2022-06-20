---
title : "EC2 Connection"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 2.4 </b> "
---

#### Connect EC2

1. Access the **AWS Management Console** interface

    - Find **EC2**
    - Select **EC2**

![Connect EC2](/images/2.4-ConnectEC2/0001.png?featherlight=false&width=90pc)

2. In **EC2** interface

    - Select **SID-security-instance**
    - Select **Connect**

![Connect EC2](/images/2.4-ConnectEC2/0002.png?featherlight=false&width=90pc)

3. In the **Connect to instance** interface

   - Select **EC2 instance Connect**
   - Select **Connect**

![Connect EC2](/images/2.4-ConnectEC2/0003.png?featherlight=false&width=90pc)

4. Successful connection

![Connect EC2](/images/2.4-ConnectEC2/0004.png?featherlight=false&width=90pc)

5. Run the following commands to set up the AWS CLI.

```
aws configure
```

   - Then use **Access key** and configure.

![Connect EC2](/images/2.4-ConnectEC2/0005.png?featherlight=false&width=90pc)

6. Create a credential file for use by the AWS CLI with the following command. This will allow you to easily switch between two different IAM users.

```
cd ~/.aws
en credentials
```

![Connect EC2](/images/2.4-ConnectEC2/0006.png?featherlight=false&width=90pc)

7. Type i and press enter to enter **insert** mode

   - Now copy and paste the updated credential file from your text editor into your vi session. It will look like the following, but with your unique Access Keys.

![Connect EC2](/images/2.4-ConnectEC2/0007.png?featherlight=false&width=90pc)

8. Press **es**c** then type **:wq!** and press **enter** to save and exit vi.


![Connect EC2](/images/2.4-ConnectEC2/0008.png?featherlight=false&width=90pc)

You will use this SSH session throughout this lab.