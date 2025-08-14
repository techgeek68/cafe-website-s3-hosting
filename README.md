# Café Website for AWS S3

A simple, stylish static website for a café—ideal for showcasing your menu, location, and contact details. Designed for easy deployment on **Amazon S3**, this site is fast, cost-effective, and requires minimal setup.

---

##  Project Structure

```
/
├── css/         # Stylesheets (e.g., `styles.css`)
├── images/      # Image assets (e.g., menu items, logo)
└── index.html   # Landing page for your café
```

---

## Features

- Fully static—built with basic HTML and CSS, no server backend required
- Lightweight and fast-loading
- Easy to customize and deploy
- Perfect for simple café landing pages

---

##  Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/techgeek68/Cafe-Website-For-AWS-S3.git
cd Cafe-Website-For-AWS-S3
```

### 2. Customize the Content

- **index.html**:
  - Edit café name, tagline, menu, hours, location, and contact info.
  - Structure semantic sections: Header, Menu, About, Footer.
- **css/**:
  - Update or add styles to match your brand—colors, fonts, layout tweaks.
- **images/**:
  - Swap out placeholder files with your café’s photos or branding assets.

### 3. View Locally

Open `index.html` in your browser to preview changes.

---

##  Deploying to Amazon S3

Follow these steps to host your site as a static website using AWS S3:

1. **Create an S3 Bucket**  
   Use your AWS Console or CLI, e.g.:

   ```bash
   aws s3api create-bucket --bucket your-unique-bucket --region us-east-1 --create-bucket-configuration LocationConstraint=us-east-1
   ```

2. **Enable Static Website Hosting**  
   In the AWS Console under **Properties**, enable static hosting and set the index document to `index.html`.

3. **Configure Public Read Access**  
   Unblock public access settings. Apply a bucket policy similar to:

   ```json
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Sid": "PublicReadGetObject",
         "Effect": "Allow",
         "Principal": "*",
         "Action": "s3:GetObject",
         "Resource": "arn:aws:s3:::your-unique-bucket/*"
       }
     ]
   }
   ```

4. **Upload Website Files**  
   Use AWS Console or CLI to upload:

   ```bash
   aws s3 sync . s3://your-unique-bucket/ --acl public-read
   ```

5. **Access Your Site**  
   Visit the S3 website endpoint (e.g., `http://your-unique-bucket.s3-website-us-east-1.amazonaws.com`).

---

##  (Optional) Advanced Enhancements

If you'd like to expand the setup further—such as adding versioning, lifecycle rules, or cross-region replication—feel free to integrate AWS best practices. While this repo is intentionally kept simple, these enhancements can provide added data protection and durability. You might refer to AWS labs that cover such practices in detail ([dev.to](https://dev.to/ameh_mathias/challenge-lab-creating-a-static-website-for-the-cafe-447i?utm_source=chatgpt.com), [medium.com](https://medium.com/%40mightytomisin/1-creating-a-static-website-for-a-caf%C3%A9-in-aws-cloud-cf9655355e75?utm_source=chatgpt.com)).

---

## Credits & License

- **Developer**: techgeek68  
- **Inspired By**: AWS static website Challenge Labs for cafés ([dev.to](https://dev.to/ameh_mathias/challenge-lab-creating-a-static-website-for-the-cafe-447i?utm_source=chatgpt.com), [medium.com](https://medium.com/%40mightytomisin/1-creating-a-static-website-for-a-caf%C3%A9-in-aws-cloud-cf9655355e75?utm_source=chatgpt.com)).  
- **License**: *(Consider adding one, e.g., MIT, if open source intended)*

---

### Ready to Get Brewing?

1. Clone and customize  
2. Deploy to S3  
3. Share your café’s story with the world!

---

Need help refining the layout or deploying it with CloudFront, SSL, or a custom domain? Just let me know—I’ve got your back!
