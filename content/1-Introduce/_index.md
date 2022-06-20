---
title : "Introduction"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

#### S3 Security Practice

In this lab, we practice security best practices for securing data in Amazon S3.

To protect your data in Amazon S3, by default, users only have access to the S3 resources they create. You can grant access to other users using one or a combination of the following access management features: **AWS Identity and Access Management (IAM)** to create users and manage access to their respective; **Access Control Lists (ACLs)** to grant user access to each object; **storage policy** to configure permissions for all objects in an S3 bucket and Query String Validation to grant limited-time access to others using a temporary URL. Amazon S3 also supports Audit Logs that list requests made to S3 resources so you get a complete view of the audience and the data accessed.

![Launch CloudFormation Template](/images/1-Introduce/s3BPIndex-02.png?featherlight=false&width=60pc)