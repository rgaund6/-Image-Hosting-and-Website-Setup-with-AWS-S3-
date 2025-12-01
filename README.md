# -Image-Hosting-and-Website-Setup-with-AWS-S3-
Amazon S3 is basically a huge online storage space provided by AWS.  Think of it like a super-safe, super-fast hard drive on the internet where you can  keep any type of file, photos, videos, documents, backups, logs, etc. 

1. Create an S3 Bucket

Open AWS Console → Search S3

Click Create bucket

Enter:

Bucket name (must be globally unique)

Region (recommended: same region for all services)

Uncheck "Block all public access"

Enable:

ACLs

Bucket public access

Click Create Bucket

🖼️ 2. Upload Images to S3

Open the bucket

Click Upload

Add:

.jpg, .png, .svg, etc.

Click Upload

Your files are now stored in S3.

🔓 3. Make Files Public

Select your uploaded image(s)

Click Actions → Make public

Confirm

You can now access each image using a URL like:

https://BUCKET-NAME.s3.amazonaws.com/image.jpg

🌐 4. Enable Static Website Hosting

Go to Bucket → Properties

Scroll down to Static website hosting

Enable it

Provide:

Index document: index.html

Error document: error.html (optional)

Copy the S3 Website Endpoint URL, example:

http://my-bucket.s3-website-us-east-1.amazonaws.com

📝 5. Upload Your Website Files

Upload:

index.html

style.css

script.js

Images

Assets

Path: S3 → Your bucket → Upload

🔧 6. Set Bucket Policy (Public Read Access)

Go to:
Permissions → Bucket Policy → Paste this:

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": [
        "s3:GetObject"
      ],
      "Resource": [
        "arn:aws:s3:::YOUR-BUCKET-NAME/*"
      ]
    }
  ]
}


👉 Replace YOUR-BUCKET-NAME

Click Save.

🌍 7. Access Your Hosted Website

Use the S3 website endpoint:

http://your-bucket-name.s3-website-region.amazonaws.com


Your static site + images are now live globally.

🔥 Features of S3 Image Hosting

Serverless (No EC2 needed)

Highly scalable

Very low cost

Fast global access

Secure with policies

Works with CloudFront CDN

📁 Project Folder Structure
/
├── index.html
├── style.css
├── script.js
└── images/
      ├── image1.jpg
      ├── image2.png
      └── logo.svg
