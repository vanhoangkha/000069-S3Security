---
title : "S3 Security Best Practices"
date : "`r Sys.Date()`"
weight : 1
chapter : false
---

# S3 Security Best Practices

In this lab, we practice security best practices for securing data in Amazon S3.

To protect your data in Amazon S3, by default, users only have access to the S3 resources they create. You can grant access to other users using one or a combination of the following access management features: **AWS Identity and Access Management (IAM)** to create users and manage access their respective; **Access Control Lists (ACLs)** to grant user access to each object; **storage policy** to configure permissions for all objects in an S3 bucket and Query String Validation to grant limited-time access to others using a temporary URL . Amazon S3 also supports Audit Logs that list requests made to S3 resources so you get a complete view of the audience and the data accessed.

![Launch CloudFormation Template](/images/1-Introduce/s3BPIndex-02.png?featherlight=false&width=60pc)

#### Content

1. [Introduction](1-introduce/)
2. [Preparation](2-prerequiste/)
3. [Require HTTPS](3-requirehttps/)
4. [Require SSE-S3 Encryption](4-requiresse/)
5. [Block Public ACLs](5-blockpublicacls/)
6. [Configure S3 Block Public Access](6-s3pba/)
7. [Restrict Access to a S3 VPC Endpoint](7-vpcendpoint/)
8. [Use AWS Config Rules to Detect a Public Bucket](8-awsconfig/)
9. [Use Amazon Access Analyzer for S3](9-accessanalyzer/)
10. [Resource Cleanup](10-cleanup/)