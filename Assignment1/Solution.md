# Assignment 1

This assignment is to create an Amazon CloudFront(CDN) for your static content website which you have to host on S3 bucket (https://xxxxxxxxx.cloudfront.net/)

Case A. If the user opens (https://xxxxxxxxx.cloudfront.net/) it should be seen "Hello, CDN origin is working fine"

    A.1 This behavior object content stays in an Edge Cache at for at least 48 hours

Case B. If the user opens (https://xxxxxxxxx.cloudfront.net/devops-folder/) it should fetch from other S3 bucket and user should see "Hello, CDN 2 origin is working fine"

    B.1 This behavior header should base caching on HOST and CloudFront-Viewer-Country



**NOTE:** Please create only one CloudFront Distribution without the Alternate Domain Names (CNAMEs) and share the CDN domain name to validate the assignment.

**NOTE:** Both the URLs should not include index.html or any .html extension.`

# Solution
