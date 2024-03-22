# Hosted a Resume Globally on AWS using S3, CloudFront, Route 53, and ACM

## Introduction
This documentation outlines the process of hosting a resume globally on Amazon Web Services (AWS) using a combination of services such as Amazon S3, CloudFront, Route 53, and ACM (AWS Certificate Manager). By following these steps, you can ensure your resume is accessible worldwide with low latency, high availability, and enhanced security.

## Prerequisites:-
Before proceeding, ensure you have the following:

- An AWS account with appropriate permissions to create and manage resources.
- Your resume file in a supported format  HTML.
## Steps:-
### Upload Resume to Amazon S3:-
1. Log in to the AWS Management Console.
2. Navigate to the Amazon S3 service.
3. Create a new S3 bucket with the same domain name i.e www.mayurbalghare.tech
4. Upload your resume file(index.html,css.style.script.js) to the selected S3 bucket.
5. Enable all the public block access.
### Configure Static Website Hosting:-
1. Select the S3 bucket containing your resume file.
2. Go to the "Properties" tab.
3. Click on "Static website hosting" and choose "Use this bucket to host a website".
4. Enter the name of your resume file index.html as the Index document.
5. Save the changes.
### Enable Public Access:-
1. While still in the bucket properties, navigate to the "Permissions" tab.
2. Click on "Bucket Policy" and add a policy to allow public read access to your resume file. Below is a sample policy:
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::www.mayurbalghare.tech/*"
        }
    ]
}
```
### Obtain SSL Certificate from ACM:-
1. Go to the ACM service in the AWS Management Console.
2. Request a new SSL certificate for your domain www.mayurbalghare.tech
3. Follow the instructions to validate the certificate  DNS validation.
4. Wait for it will take time at least 30 minutes and we have to request certificate  in North virginia(US-EAST-1)
### Configure CloudFront Distribution:-
1. Navigate to the CloudFront service in the AWS Management Console.
2. Click on "Create Distribution" and select "Get Started" under the Web delivery method.
3. Configure the distribution settings:
    - Origin Domain Name: Select the S3 bucket endpoint.
    - Viewer Protocol Policy: Redirect HTTP to HTTPS.
    - SSL Certificate: Choose the SSL certificate obtained from ACM (if applicable).
    - Enable "Compress Objects Automatically" for better performance.
4. Complete the distribution setup and wait for it to deploy.
###  Route 53 Configuration:-
1. Go to the Route 53 service in the AWS Management Console.
2. Create a new hosted zone for your domain www.mayurbalghare.tech
3. Add a new record set:
    - Name: Enter your desired subdomain (www)
    - Type: Choose "A - IPv4 address".
    - Alias: Yes.
    - Alias Target: Select the CloudFront distribution created in the previous step.
4. Save the record set. 
## Conclusion:-
Resume(Interactive Resume-Ashwin) is now hosted globally on AWS, utilizing S3 for storage, CloudFront for content delivery, Route 53 for DNS management, and optionally ACM for SSL certificate provisioning. Test the accessibility of your resume website from different regions to ensure global availability. You can further enhance your website's performance and security by configuring caching settings, enabling logging, and implementing other AWS services as needed.

