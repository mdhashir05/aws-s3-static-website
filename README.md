# AWS S3 Static Website Hosting

A hands-on AWS cloud project demonstrating the deployment of a static website using **Amazon S3 Static Website Hosting**. The website uses HTML, CSS, and JavaScript and is served through an S3 website endpoint without requiring a traditional web server.

## Project Overview

This project demonstrates how Amazon S3 can host static website content using object storage and website hosting configuration. The implementation includes creating an S3 bucket, uploading website files, enabling static website hosting, configuring public read access, and verifying the website through a browser.

**Project status:** The website was successfully deployed and tested during the project. Check the current availability of the endpoint before presenting it as a live website.

## Project Objectives

- Create and configure an Amazon S3 bucket.
- Upload HTML, CSS, and JavaScript website files.
- Enable S3 Static Website Hosting.
- Configure the index document.
- Set up a bucket policy for public object read access.
- Test website accessibility and client-side functionality through the S3 website endpoint.

## AWS Services Used

This project intentionally uses **Amazon S3 only** for its cloud implementation.

| Service or Feature | Purpose |
|---|---|
| Amazon S3 | Stores the website files |
| S3 Static Website Hosting | Serves the static website through an S3 website endpoint |
| S3 Bucket Policy | Controls public read access to website objects |

No EC2, Lambda, CloudFront, RDS, VPC, or other AWS services were used in this implementation.

## Architecture

![AWS S3 Static Website Architecture](architecture-diagram.png)

### Architecture Flow

**User / Internet → S3 Website Endpoint → Amazon S3 Static Website Hosting → Website Content Rendered in Browser**

The S3 bucket contains three website files:

- `index.html` — Main webpage structure and content.
- `style.css` — Website layout, styling, and appearance.
- `script.js` — Client-side JavaScript functionality.

The browser loads the HTML document and retrieves the associated CSS and JavaScript files from the S3 website endpoint.

## S3 Bucket Configuration

| Configuration | Value |
|---|---|
| AWS Service | Amazon S3 |
| Bucket Name | `hashir-static-website` |
| AWS Region | `us-east-1` (US East — N. Virginia) |
| Hosting Type | S3 bucket website hosting |
| Static Website Hosting | Enabled during deployment |
| Index Document | `index.html` |
| Website Files | `index.html`, `style.css`, `script.js` |
| Storage Class | S3 Standard |
| Requester Pays | Disabled |

### Website Endpoint

The website was accessed through the following S3 website endpoint:

```text
http://hashir-static-website.s3-website-us-east-1.amazonaws.com
```

The endpoint reflects the original project configuration. Its current availability depends on the bucket, hosting configuration, and access permissions still being in place.

## Website Implementation

### `index.html`

Contains the main structure and content of the static website. It acts as the website's entry point and references the stylesheet and JavaScript file.

### `style.css`

Defines the visual appearance of the website, including styling, layout, and presentation.

### `script.js`

Provides client-side JavaScript functionality executed in the visitor's browser.

## Deployment and Configuration

The following implementation steps were completed during the project:

1. Created an S3 bucket named `hashir-static-website` in the `us-east-1` region.
2. Uploaded `index.html`, `style.css`, and `script.js` to the bucket.
3. Enabled S3 Static Website Hosting.
4. Configured `index.html` as the index document.
5. Configured a bucket policy granting public read access to website objects.
6. Accessed the website through the generated S3 website endpoint.
7. Tested the website in a browser and verified that the page loaded successfully.

## Bucket Policy and Access Control

Public read access was configured to allow visitors to retrieve the website files.

The policy used the following access pattern:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::hashir-static-website/*"
    }
  ]
}
```

This policy grants anonymous read access to objects within the specified bucket. It does not grant visitors permission to upload, modify, or delete objects.

**Security consideration:** Public access was intentionally configured for this static website demonstration. Only public website assets should be stored in such a bucket. AWS Block Public Access settings and account-level policies must also permit the intended configuration.

## Implementation Evidence

### 1. S3 Bucket

![S3 Bucket](screenshots/01-s3-bucket.png)

Documents the creation of the `hashir-static-website` bucket in the selected AWS region.

### 2. Uploaded Website Files

![S3 Objects](screenshots/02-s3-objects.png)

Shows the website files stored in the bucket: `index.html`, `style.css`, and `script.js`.

### 3. Static Website Hosting

![Static Website Hosting](screenshots/03-static-website-hosting.png)

Documents the static website hosting configuration and the `index.html` index document.

### 4. Bucket Policy

![S3 Bucket Policy](screenshots/04-bucket-policy.png)

Shows the bucket policy configured to allow public read access to the website objects.

### 5. Deployed Website

![Deployed Website](screenshots/05-deployed-website.png)

Provides evidence that the static website was successfully opened through the S3 website endpoint during testing.

## Testing Results

The website was tested during deployment to verify the S3 configuration and browser behavior.

| Test Case | Expected Result | Recorded Result |
|---|---|---|
| S3 bucket creation | Bucket created in `us-east-1` | Passed during testing |
| Website file upload | Three website files stored in the bucket | Passed during testing |
| Static website hosting | Hosting enabled | Passed during testing |
| Index document | `index.html` displayed as the home page | Passed during testing |
| Website endpoint | Website opens in a browser | Passed during testing |
| CSS loading | Website styling appears correctly | Passed during testing |
| JavaScript functionality | Client-side JavaScript executes | Passed during testing |

These results describe the original deployment tests; they do not independently confirm the current state of the AWS resources.

## Key Skills Demonstrated

- Amazon S3 bucket creation and configuration.
- Static website hosting using an S3 website endpoint.
- Uploading and organizing website assets in object storage.
- Configuring index document settings.
- Writing and applying an S3 bucket policy.
- Understanding public object access and AWS access controls.
- Deploying and testing an HTML, CSS, and JavaScript website.
- Verifying cloud deployments through console screenshots and browser testing.
- Documenting cloud architecture and implementation results.

## Security and Limitations

- The S3 website endpoint uses HTTP rather than HTTPS.
- The configured public-read policy makes website objects publicly retrievable.
- S3 static website hosting serves static content and does not execute server-side PHP, Python, or other backend application code.
- Sensitive files, credentials, and private information must not be uploaded to a publicly readable bucket.
- HTTPS delivery and a custom domain could be considered as future improvements, potentially using Amazon CloudFront.

## Conclusion

This project demonstrates how Amazon S3 can be used to host and serve a static website without provisioning or managing a traditional web server. By configuring bucket hosting, uploading website assets, applying a bucket policy, and testing the endpoint, the project illustrates the fundamentals of static web hosting and cloud-based object storage on AWS.

## Project Architecture Summary

```text
User / Internet
       |
       v
S3 Website Endpoint
       |
       v
Amazon S3
       |
       v
Static Website Hosting
       |
       +----> index.html
       |
       +----> style.css
       |
       +----> script.js
       |
       v
Website Rendered in Browser
```

## Repository Structure

```text
aws-s3-static-website/
├── README.md
├── architecture-diagram.png
├── index.html
├── style.css
├── script.js
└── screenshots/
    ├── 01-s3-bucket.png
    ├── 02-s3-objects.png
    ├── 03-static-website-hosting.png
    ├── 04-bucket-policy.png
    └── 05-deployed-website.png
```

---

**Author:** Mohammed Hashir  

**Project:** AWS S3 Static Website Hosting  

**Cloud Platform:** Amazon Web Services (AWS)
