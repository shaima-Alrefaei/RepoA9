
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
![screenshot](https://github.com/shaima-Alrefaei/RepoA9/blob/main/part11.png?raw=true)

### P2:
![screenshot](https://github.com/shaima-Alrefaei/RepoA9/blob/main/Welcome%20to%20Clarusway%20Bootcamp.png?raw=true)

### Terminal Output : 
![screenshot](https://github.com/shaima-Alrefaei/RepoA9/blob/main/part1TerminalOutput.png?raw=true)

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
![screenshot](https://github.com/shaima-Alrefaei/RepoA9/blob/main/Part22%20EC2%20Instances%20running.png?raw=true)

### ASG configuration details: 
![screenshot](https://github.com/shaima-Alrefaei/RepoA9/blob/main/Part2ASG%20configuration%20details.png?raw=true)
![screenshot](https://github.com/shaima-Alrefaei/RepoA9/blob/main/Part2ASG%20configuration%20details2.png?raw=true)



---

## 🌐 Application Load Balancer (ALB)

DNS name :  clarusway-alb-1490677511.eu-north-1.elb.amazonaws.com
### ALB DNS output screenshot : 
![screenshot](https://github.com/shaima-Alrefaei/RepoA9/blob/main/DNSOutput1.png?raw=true)
![screenshot](https://github.com/shaima-Alrefaei/RepoA9/blob/main/DNSOutput2.png?raw=true)

### ✅ Testing Round-Robin Behavior
```bash
for i in {1..5}; do curl -s clarusway-alb-1490677511.eu-north-1.elb.amazonaws.com ; done
```
![screenshot](https://github.com/shaima-Alrefaei/RepoA9/blob/main/ELB-output.png?raw=true)




