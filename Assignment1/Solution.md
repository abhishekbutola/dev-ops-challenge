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

<img width="697" alt="image" src="https://github.com/user-attachments/assets/96af82d9-9cdc-4a53-a95e-9029c7402535">

   "Hello, CDN origin is working fine"

 then create a folder devops-folder in s3 bucket (dev-challenge-bucket2) and upload index.html 

<img width="603" alt="image" src="https://github.com/user-attachments/assets/ee658ce6-54aa-419d-8fd1-a632ec79841a">

<img width="620" alt="image" src="https://github.com/user-attachments/assets/cf58c2bb-55c5-4440-b125-571537db2522">

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

<img width="673" alt="image" src="https://github.com/user-attachments/assets/1a4d10b1-c8bb-4db6-bc61-8613c78f6dee">

   
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

<img width="580" alt="image" src="https://github.com/user-attachments/assets/09cc8747-0129-40a7-9874-f43756bbfe8e">


7. Enable Static hosting and access the page2 via
    http://dev-challenge-bucket2.s3-website-us-east-1.amazonaws.com/index.html

<img width="614" alt="image" src="https://github.com/user-attachments/assets/756242f6-1b77-4765-b91b-a5336153d051">


Cloud Front 

7. Go to AWS , search for cloud front and Create a distributions
8. Add both s3 dev-challenge-bucket1 and dev-challenge-bucket2 buckets as origins

<img width="800" alt="image" src="https://github.com/user-attachments/assets/0bb49e0d-a5d9-485a-ae70-3c7540ee7d01">


<img width="795" alt="image" src="https://github.com/user-attachments/assets/e40358c9-fe32-41c7-909f-1e6a5214307d">

9. In case of origin dev-challenge-bucket1.s3.us-east-1.amazonaws.com
    make sure root folder / is pointed to index.html of the dev-challenge-bucket1 (found in the     general section of distribution)

<img width="799" alt="image" src="https://github.com/user-attachments/assets/3bcf216d-3719-4e7a-8c65-617f618ea72a">

10. create distribution
<img width="800" alt="image" src="https://github.com/user-attachments/assets/9e0e405b-78c7-4f01-b623-7d872acd6f9e">

11. Test the behaviour of the distribution by accessing 
    https://d361dcs130gtue.cloudfront.net/index.html

<img width="417" alt="image" src="https://github.com/user-attachments/assets/0cf1ad6f-c1b4-493a-b9a7-951bb2f96682">

    https://d361dcs130gtue.cloudfront.net/devops-folder/index.html

<img width="438" alt="image" src="https://github.com/user-attachments/assets/30b04f3a-a6f0-4b02-aa69-ce76712e791d">


12. Add behaviour for dev-challenge-bucket2
   /devops-folder/*
   in origin group select bucket dev-challenge-bucket2
<img width="488" alt="image" src="https://github.com/user-attachments/assets/351735eb-f476-420b-a807-3ecc73303db9">


13. Access it over
    https://d361dcs130gtue.cloudfront.net/

<img width="365" alt="image" src="https://github.com/user-attachments/assets/ae84839b-1b29-44c6-b3ab-b9cc73fd8e7e">

and 
    https://d361dcs130gtue.cloudfront.net/devops-folder/

