# Assignment: Host Static Website on Amazon S3

## Objective

Host a static HTML website using an Amazon S3 bucket.

## Prerequisites

* AWS Account
* AWS S3
* HTML file
* AWS CLI (optional)

## Steps

### 1. Create an S3 Bucket

1. Log in to the AWS Management Console.
2. Go to **S3**.
3. Click **Create bucket**.
4. Enter a unique bucket name.
5. Select the required AWS Region.
6. Create the bucket.

### 2. Upload the HTML File

1. Open the created S3 bucket.
2. Click **Upload**.
3. Select the `index.html` file.
4. Click **Upload**.

### 3. Enable Static Website Hosting

1. Open the S3 bucket.
2. Go to **Properties**.
3. Find **Static website hosting**.
4. Click **Edit**.
5. Select **Enable**.
6. Select **Host a static website**.
7. Enter:

```text
Index document: index.html
```

8. Click **Save changes**.

### 4. Configure Bucket Permissions

If public access is required for the website:

1. Go to **Permissions**.
2. Edit **Block public access**.
3. Disable **Block all public access** as appropriate.
4. Confirm the warning.

### 5. Add Bucket Policy

Go to:

**S3 → Bucket → Permissions → Bucket policy**

Add a policy that allows public read access to the website objects.

Example:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::YOUR-BUCKET-NAME/*"
    }
  ]
}
```

Replace:

```text
YOUR-BUCKET-NAME
```

with your actual S3 bucket name.

### 6. Test the Website

1. Go back to **Properties**.
2. Find **Static website hosting**.
3. Copy the **Bucket website endpoint**.
4. Open the endpoint in a browser.

The `index.html` page should be displayed.

## Architecture

```text
User
  |
  v
Internet
  |
  v
Amazon S3 Bucket
  |
  v
index.html
  |
  v
Static Website
```

## Result

The static HTML website was successfully hosted on **Amazon S3** and accessed using the S3 static website endpoint.

## Technologies Used

* Amazon S3
* HTML
* AWS Management Console

