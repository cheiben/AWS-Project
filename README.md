# AWS Static Website Hosting Project

## Introduction

This hands-on lab guides you through hosting static web content in an Amazon S3 bucket, protected and accelerated by Amazon CloudFront. The skills learned will help you secure your workloads in alignment with the [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/).

## Project Overview

This project demonstrates how to:
- Create a secure S3 bucket for static content
- Upload web files to the bucket
- Configure CloudFront as a content delivery network
- Implement security best practices

## Steps

### 1. Create S3 Bucket

1. Open the [Amazon S3 console](https://console.aws.amazon.com/s3/)
2. From the console dashboard, choose **Create bucket**
3. Enter a **Bucket name** following these naming guidelines:
   - Must be unique across all existing bucket names in Amazon S3
   - Must not contain uppercase characters
   - Must start with a lowercase letter or number
   - Must be between 3 and 63 characters long
4. Choose an **AWS Region** close to you to minimize latency and costs
5. Accept default value for **Block all public access** (CloudFront will serve the content)
6. Enable **bucket versioning** to protect against accidental modifications or deletions

### 2. Upload Example Index.HTML File

1. Create a simple index.html file with the following content:
   ```html
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
   ```
2. Open the [Amazon S3 console](https://console.aws.amazon.com/s3/)
3. Click the name of your newly created bucket
4. Click the **Upload** button
5. Select and upload your index.html file

### 3. Configure Amazon CloudFront

1. Open the [Amazon CloudFront console](https://console.aws.amazon.com/cloudfront/home)
2. From the console dashboard, click **Create Distribution**
3. Click **Get Started** in the Web section
4. Configure the distribution:
   * In the **Origin Domain Name** field, select the S3 bucket you created previously
   * In **Origin Access**, click "Legacy access identity" then click **Create a New OAI**
   * Click the **Yes, Update Bucket Policy** button
   * Scroll down to the **Settings** section, in the **Default Root Object** field enter `index.html`
   * Click **Create Distribution**
5. Wait approximately 10 minutes until the distribution status changes from "In Progress" to "Deployed"
6. Test your setup by accessing the CloudFront Domain Name (found in the console) in a web browser

For more information on other configuration options, see the [CloudFront documentation](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-web-values-specify.html).

### 4. Tear Down

#### Delete the CloudFront distribution:

1. Open the [Amazon CloudFront console](https://console.aws.amazon.com/cloudfront/home)
2. Select the distribution you created and click the **Disable** button
3. Confirm by clicking **Yes, Disable**
4. After approximately 15 minutes when the status is "Disabled", select the distribution and click **Delete**
5. Confirm by clicking **Yes, Delete**

#### Delete the S3 bucket:

1. Open the [Amazon S3 console](https://console.aws.amazon.com/s3/)
2. Check the box next to your bucket, then click **Empty**
3. Confirm emptying the bucket
4. Once the bucket is empty, check the box next to it and click **Delete**
5. Confirm deletion

## Security Considerations

- The S3 bucket is secured by default with all public access blocked
- CloudFront provides secure access to the S3 content
- Consider enabling additional security options such as logging and encryption
- For more information, see [Protecting Data in Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/security-best-practices.html)

## Additional Resources

- [Introduction to Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)
- [Amazon CloudFront Documentation](https://docs.aws.amazon.com/cloudfront/)
- [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)
