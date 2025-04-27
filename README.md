# Run your static website on AWS

Draft mode - update 27 April 2025

There are a couple ways to host a static webite on AWS.  If you want support for TLS, you will need to use CloudFront.

#### Creating a static webiste
1. Upload your static site an s3 bucket and enable Static website hosting
2. Use Amplify with your s3 bucket.  This generates all the necessary AWS resource to run a static website
3. Use an s3 bucket to hold your site pages and then setup a TLS certificate, a CloudFrount distirbution and Route 53 for DNS

### S3 Bucket Static Website Hosting
* Create an S3 bucket.  I name te S3 bucket something like this mywebsite.com
* Upload your website the s3 bucket
* In S3 bucket choose the Properties tab.  Scroo to the boton of the page and click the Edit button Static Website hosting section
  * Enable Static website hosting
  * For Hosting type choose Host a static website
  * Fill in the Index document text field - I use index.html
  * Click the oragne Save changes button in the bottom right hand corner


