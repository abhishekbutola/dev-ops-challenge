# Assignment 1

This assignment is to create an Amazon CloudFront(CDN) for your static content website which you have to host on S3 bucket (https://xxxxxxxxx.cloudfront.net/)

Case A. If the user opens (https://xxxxxxxxx.cloudfront.net/) it should be seen "Hello, CDN origin is working fine"

    A.1 This behavior object content stays in an Edge Cache at for at least 48 hours

Case B. If the user opens (https://xxxxxxxxx.cloudfront.net/devops-folder/) it should fetch from other S3 bucket and user should see "Hello, CDN 2 origin is working fine"

    B.1 This behavior header should base caching on HOST and CloudFront-Viewer-Country



**NOTE:** Please create only one CloudFront Distribution without the Alternate Domain Names (CNAMEs) and share the CDN domain name to validate the assignment.

**NOTE:** Both the URLs should not include index.html or any .html extension.`

# Solution

Steps to follow:

1. Login to your AWS account
2. Create 2 s3 bucket dev-challenge-bucket1, dev-challenge-bucket2 and upload index.html in dev-challenge-bucket1

   "Hello, CDN origin is working fine"

 then create a folder devops-folder in s3 bucket (dev-challenge-bucket2) and upload index.html 

   "Hello, CDN 2 origin is working fine"

4. set bucket1 policy

   {
   "Version": "2012-10-17",
   "Statement": [
   {
   "Sid": "PublicRead",
   "Effect": "Allow",
   "Principal": "*",
   "Action": "s3:GetObject",
   "Resource": "arn:aws:s3:::dev-challenge-bucket1/*"
   }
   ]
   }
5. set bucket2 policy

    {
"Version": "2012-10-17",
"Statement": [
{
"Sid": "PublicRead",
"Effect": "Allow",
"Principal": "*",
"Action": "s3:GetObject",
"Resource": "arn:aws:s3:::dev-challenge-bucket2/*"
}
]
}

6. Enable Static hosting and access the page1 via
    http://dev-challenge-bucket1.s3-website-us-east-1.amazonaws.com/index.html
7. Enable Static hosting and access the page2 via
    http://dev-challenge-bucket2.s3-website-us-east-1.amazonaws.com/index.html


Cloud Front 

7. Go to AWS , search for cloud front and Create a distributions
8. Add both s3 dev-challenge-bucket1 and dev-challenge-bucket2 buckets as origins
9. In case of origin dev-challenge-bucket1.s3.us-east-1.amazonaws.com
    make sure root folder / is pointed to index.html of the dev-challenge-bucket1 (found in the     general section of distribution)
10. create distribution
11. Test the behaviour of the distribution by accessing 
    https://d361dcs130gtue.cloudfront.net/index.html
    https://d361dcs130gtue.cloudfront.net/devops-folder/index.html

12. Add behaviour for dev-challenge-bucket2
   /devops-folder/*
   in origin group select bucket dev-challenge-bucket2

13. Access it over
    https://d361dcs130gtue.cloudfront.net/
and 
    https://d361dcs130gtue.cloudfront.net/devops-folder/

