# AWS-Project


Introduction

This hands-on lab will guide you through the steps to host static web content in an Amazon S3 bucket, protected and accelerated by Amazon CloudFront. Skills learned will help you secure your workloads in alignment with the AWS Well-Architected Framework.
ref:  https://aws.amazon.com/architecture/well-architected/

Steps:
1 Create S3 bucket
2 Upload example index.html file
3 Configure Amazon CloudFront
4 Tear down


********************************************* Work Flow ***************************************************************

1 CREATE S3 BUCKET
Create an Amazon S3 bucket to host static content using the Amazon S3 console. For more information about Amazon S3, see Introduction to Amazon S3.

Open the Amazon S3 console at https://console.aws.amazon.com/s3/.
From the console dashboard, choose Create bucket.
s3-create-bucket-1

Enter a Bucket name for your bucket, type a unique DNS-compliant name for your new bucket. Follow these naming guidelines:
The name must be unique across all existing bucket names in Amazon S3.
The name must not contain uppercase characters.
The name must start with a lowercase letter or number.
The name must be between 3 and 63 characters long.
Choose an AWS Region where you want the bucket to reside. Choose a Region close to you to minimize latency and costs, or to address regulatory requirements. Note that for this example we will accept the default settings and this bucket is secure by default. Consider enabling additional security options such as logging and encryption, the S3 documentation has additional information such as Protecting Data in Amazon S3.
Accept default value for Block all public access as CloudFront will serve the content for you from S3.
Enable bucket versioning, to keep multiple versions of an object so you can recover an object if you unintentionally modify or delete it.

2 UPLOAD EXAMPLE INDEX.HTML FILE

a. Create a simple index.html file, you can create by coping the following text into your favourite text editor.

<!DOCTYPE html>
<html>
  <head>
    <title>Hello World</title>
  </head>
  <body>
    <h1>CHEIBEN</h1>
    <p>Example paragraph.</p>
  </body>
</html>

b. Open the Amazon S3 console at https://console.aws.amazon.com/s3/.
c. In the console click the name of your bucket you just created.
d. Click the Upload button.

3. CONFIGURE AMAZON CLOUDFRONT

Using the AWS Management Console, we will create a CloudFront distribution, and configure it to serve the S3 bucket we previously created.

a. Open the Amazon CloudFront console at https://console.aws.amazon.com/cloudfront/home.
b. From the console dashboard, click Create Distribution.
c. Click Get Started in the Web section.
d. Specify the following settings for the distribution:
   * In the Origin Domain Name field Select the S3 bucket you created previously.
   * In Origin Access click "Legacy access identity" then click Create a New OAI.
   * Click the Yes, Update Bucket Policy Button.
   * Scroll down to the  Settings section, in the Default Root Object field enter *index.html*
   * Click Create Distribution
   * To return to the main CloudFront page click Distributions from the left navigation menu
   * For more information on the other configuration options, see https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-web-values-specify.html documentation.

e. After CloudFront creates your distribution which may take approximately 10 minutes, the value of the Status column for your distribution will change from In Progress to Deployed.

f. When your distribution is deployed, confirm that you can access your content using your new CloudFront Domain Name which you can see in the console. Copy the Domain Name into a web browser to test.

4 TEAR DOWN
The following instructions will remove the CloudFront distribution and S3 bucket created in this lab.

Delete the CloudFront distribution:

Open the Amazon CloudFront console at (https://console.aws.amazon.com/cloudfront/home).
From the console dashboard, select the distribution you created earlier and click the Disable button. To confirm, click the Yes, Disable button.
After approximately 15 minutes when the status is Disabled, select the distribution and click the Delete. button, and then to confirm click the Yes, Delete button.
Delete the S3 bucket:

Open the Amazon S3 console at https://console.aws.amazon.com/s3/.
Check the box next to the bucket you created previously, then click Empty from the menu.
Confirm the bucket you are emptying.
Once the bucket is empty check the box next to the bucket, then click Delete from the menu.
Confirm the bucket you are deleting.
