# Run your static website on AWS

Draft mode - update 27 April 2025

There are a couple ways to host a static webite on AWS.  If you want support for TLS, you will need to use CloudFront.

#### Creating a static webiste
1. Upload your static site an s3 bucket and enable Static website hosting
2. Use Amplify with your s3 bucket.  This generates all the necessary AWS resource to run a static website
3. Use an s3 bucket to hold your site pages and then setup a TLS certificate, a CloudFrount distirbution and Route 53 for DNS

#### S3 Bucket Static Website Hosting
* Create an S3 bucket.  I name te S3 bucket something like this mywebsite.com
* Upload your website the s3 bucket
* In S3 bucket choose the Properties tab.  Scroo to the boton of the page and click the Edit button Static Website hosting section
  * Enable Static website hosting
  * For Hosting type choose Host a static website
  * Fill in the Index document text field - I use index.html
  * Click the oragne Save changes button in the bottom right hand corner
  * Make a note Bucket Website Endpoint so can test access after updating the Permissions tab
  * Make a note of your Amazon Resource Name (ARN) before you move on to the next step
 
* In the S3 bucket next choose the Permissions tab and go to the Bucket Policy ection
  * Click the edit button in the Bucket Policy and use this JSON text.  Use the ARN name for you bucket for the Resouce 
 ```
 {
     "Version": "2012-10-17",
     "Statement": [
         {
             "Sid": "PublicReadGetObject",
             "Effect": "Allow",
             "Principal": "*",
             "Action": "s3:GetObject",
             "Resource": "arn:aws:s3:::<arn>/*"
         }
     ]
}
```

### An easier way to upload your data

We will create a credential to access our specific S3 bucket and the AWS command line to upload our static website from our computer.  I'm using a Mac in this example, but this should be applicable to any Linux machine and at least provide a starting point for a Windows user.  If your content updates on a regular basis, with the Mac and Linux you can use a cronjob to automatically up new web content for you.

* Go to the Identity and Access Management section of AWS to create a Group and User.  If you will only one user updating your content you can skip creating a group.  In the example we will do it for completeness

* On the right hand menu bar, click User Grops, and then click the organge Create group button
 * Give your group a name 
  * Click the orange save changes button
  * Test your S3 static bucket website URL it would look someething like this - http://<arn>.s3-website.us-east-2.amazonaws.com 


