# AWS-Static-page-hosting

# Deploying a Static Website using AWS S3

This guide provides step-by-step instructions on how to deploy a static website (HTML, CSS, JavaScript) using an AWS S3 bucket. AWS S3 (Simple Storage Service) is an object storage service that offers industry-leading scalability, data availability, security, and performance.

![static architecture drawio](https://github.com/user-attachments/assets/f32b5af9-46a6-45f6-9c67-aaa738363052)


## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Create an S3 Bucket](#create-an-s3-bucket)
3. [Upload Your Website Files](#upload-your-website-files)
4. [Enable Static Website Hosting](#enable-static-website-hosting)
5. [Set Permissions](#set-permissions)
6. [Access Your Website](#access-your-website)
7. [Configure Custom Domain (Optional)](#configure-custom-domain-optional)
8. [Add Images](#add-images)

## Prerequisites

Before starting, ensure you have:

- An AWS account. If you don’t have one, [create an AWS account](https://aws.amazon.com/free/).
- A static website(HTML, CSS, Javascript)

## Create an S3 Bucket

1. **Log in to AWS Management Console**: Navigate to the [S3 Console](https://s3.console.aws.amazon.com/s3/home).
2. **Create a Bucket**:
   
   ![search S3](https://github.com/user-attachments/assets/e537f96a-150d-4e56-ac38-3aad74a37041)
   
   - Click on the **Create bucket** button.
   - Enter a unique bucket name (e.g., `peterportfolio`).
     
     ![name bucket](https://github.com/user-attachments/assets/fe0be9c3-3c4d-4841-812d-38e0b4121fbb)
     
   - Choose a region close to your target audience.
   - Uncheck "block public access" button to make your bucket public and accessible by users.
     
     ![make bucket accessible to public](https://github.com/user-attachments/assets/5eb103fb-1b4a-4843-a20f-bc820a1b36ba)
     
   - Leave other settings as default and click **Create bucket**.

Creating an S3 bucket is essential as it will be the container that holds all your static website files and assets.

![bucket saved](https://github.com/user-attachments/assets/a56eae1a-cda2-4949-97cd-5277ef782a8d)

## Upload Your Website Files

1. **Navigate to Your Bucket**:
   - Click on the bucket name you created.
2. **Upload Files**:
   - Click the **Upload** button.
   - Drag and drop your website files (HTML, CSS, JavaScript) or use the **Add files** button.
     
     ![upload static files](https://github.com/user-attachments/assets/eb2f2b65-ee45-462b-b55b-fdb967b80635)
     
   - Click **Upload**.
     
     ![static files uploaded](https://github.com/user-attachments/assets/c7486e4d-a128-4076-8e28-2e976af04cdc)

Uploading your website files to S3 ensures that all your static content is stored in the cloud, making it accessible over the internet.

## Enable Static Website Hosting

1. **Bucket Properties**:
   - Navigate to the **Properties** tab.
2. **Enable Static Website Hosting**:
   - Scroll down to the **Static website hosting** section and click **Edit**.
   - Select **Enable**.
   - For **Index document**, enter `index.html`.
   - For **Error document** (optional), enter `error.html`.
   - Click **Save changes**.
   - 
     ![enable static file hosting](https://github.com/user-attachments/assets/b540dfe2-cc69-4484-b8b9-bb97e6430e88)

Enabling static website hosting configures the S3 bucket to serve web pages directly. The index document is the default file that will be served when users access your website.

## Set Permissions

1. **Bucket Permissions**:
   - Navigate to the **Permissions** tab.
2. **Bucket Policy**:
   - Scroll to the **Bucket policy** section and click **Edit**.
   - Paste the following policy to make the bucket content publicly accessible:

   ```json
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Sid": "PublicReadGetObject",
         "Effect": "Allow",
         "Principal": "*",
         "Action": "s3:GetObject",
         "Resource": "arn:aws:s3:::my-bucket-name/*"
       }
     ]
   }

   
![policy](https://github.com/user-attachments/assets/d4adf04b-9aa7-4da2-82b8-acc8d28e8aff)

 - Replace "my-bucket-name" with your bucket name.
 - Click Save changes.
     
Setting permissions allows your website to be accessible to the public. The bucket policy grants read access to all objects in the bucket.

## Access Your Website
### Obtain the Endpoint

Go to the Properties tab.
In the Static website hosting section, find the Bucket website endpoint URL.
### Access the URL:

![website endpoint](https://github.com/user-attachments/assets/4c264842-7c32-4dac-b8c9-b2da759143ed)

Open the URL in your web browser.

![url](https://github.com/user-attachments/assets/900aa53d-1f0a-435f-ad0a-d44db823211a)

The endpoint URL is the web address of your static website, making it accessible over the internet.

## Configure Custom Domain (Optional)
Register a Domain: Use Amazon Route 53 or any domain registrar.
### Configure DNS:
Point your domain to the S3 bucket endpoint using CNAME records.
### Update Bucket Policy:
Modify the bucket policy to include the custom domain.

Configuring a custom domain provides a branded and memorable URL for your website, improving accessibility and user experience.

## Add Images

### Upload Images:
Follow the same steps as uploading website files.
Referencing Images:
Ensure image paths in your HTML/CSS files are correct.
Adding images enhances the visual appeal of your website. Properly referencing them ensures they are displayed correctly.


