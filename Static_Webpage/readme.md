# Dog Gallery – Static Website Hosting using Amazon S3

This project demonstrates how to host a simple static HTML website (Dog Image Gallery) using **Amazon S3 Static Website Hosting**.

---

## Steps to Deploy

### 1️. Create an S3 Bucket

* Go to AWS Console -> S3
* Click **Create Bucket**
* Enter a unique bucket name
   Example: `dogs-variety`
* Select region
* Keep default settings -> Click **Create**

---

### 2️. Upload Website Files

* Open your bucket
* Go to **Objects**
* Click **Upload**
* Upload your HTML file (e.g., `index.html`)
* Click **Upload**

---

### 3️. Enable Static Website Hosting

* Go to **Properties**
* Scroll to **Static Website Hosting**
* Click **Edit**
* Enable:

  * **Enable static website hosting**
  * Index document: `index.html`
* Save changes

Copy the **Bucket Website Endpoint URL**
Example:

```
http://dogs-variety.s3-website-us-east-2.amazonaws.com
```

---

### 4️. Disable Block Public Access

* Go to **Permissions**
* Click **Block Public Access (Edit)**
* Uncheck:

  * Block all public access
* Save changes

---

### 5️. Add Bucket Policy

Go to:

```
Permissions -> Bucket Policy
```

Paste the following policy:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::dogs-variety/*"
    }
  ]
}
```

**Important:**
Make sure the bucket name matches exactly:

```
dogs-variety
```

---

## Access Your Website

Open the endpoint URL in your browser:

```
http://dogs-variety.s3-website-us-east-2.amazonaws.com
```

You should see your **Dog Image Gallery** live 

---

