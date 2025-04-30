
# Week-9 Assignment - Clarusway Infrastructure Bootcamp

## 🏗️ Project: AWS Web Application Deployment (S3 + ALB + ASG)

---

## 📁 Static Website (S3)

### ✅ Bucket Name
`shaima-clarusway-assets` 

### ✅ Files Hosted
- `index.html`
- `logo.png`
- `sda.png`

### ✅ Sample Access
```bash
curl -I http://shaima-clarusway-assets.s3-website.eu-north-1.amazonaws.com
```
### Deliverables:
### P1:

### P2:

### Terminal Output : 

---

## ⚙️ Launch Template & ASG

### ✅ Launch Template Configuration

```bash
#!/bin/bash
yum update -y
yum install nginx -y
systemctl start nginx
systemctl enable nginx
aws s3 cp s3://shaima-clarusway-assets/index.html /usr/share/nginx/html/
aws s3 cp s3://shaima-clarusway-assets/logo.png /usr/share/nginx/html/
aws s3 cp s3://shaima-clarusway-assets/sda.png /usr/share/nginx/html/
echo "<p>Hostname: $(hostname)</p>" >> /usr/share/nginx/html/index.html
```


### Screenshot of 2 running instances : 

### ASG configuration details: 



---

## 🌐 Application Load Balancer (ALB)

DNS name :  clarusway-alb-1490677511.eu-north-1.elb.amazonaws.com
### ALB DNS output screenshot : 


### ✅ Testing Round-Robin Behavior
```bash
for i in {1..5}; do curl -s clarusway-alb-1490677511.eu-north-1.elb.amazonaws.com ; done
```



