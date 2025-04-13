Static Website Hosting on AWS EC2 (Apache2)

Overview
This project explains how to deploy a static website on an AWS EC2 instance using the Apache2 web server. Security groups are configured to allow HTTP and HTTPS traffic.

1. Launch an EC2 Instance
• Go to the AWS Management Console.
• Launch a new EC2 instance (Ubuntu or Amazon Linux recommended).
• Set key pair for SSH access.
• Assign or create a Security Group (firewall) that initially allows SSH (port 22).

2. Connect to the EC2 Instance
• SSH into your instance using the terminal:
ssh -i your-key.pem ec2-user@your-ec2-public-ip

3. Install Apache2 Web Server
• Update the package list:
sudo apt update
• Install Apache2:
sudo apt install apache2 -y

4. Deploy Static Website Files
• Upload your HTML, CSS, JS, and image files to the web server directory:
sudo cp -r your-website-files/* /var/www/html/

5. Configure Security Group for HTTP/HTTPS
• Open EC2 dashboard → Instances → Select your instance → Security → Edit Inbound Rules.
• Add:
HTTP (Port 80) - Anywhere (0.0.0.0/0)
HTTPS (Port 443) - Anywhere (0.0.0.0/0)

6. Access the Website
• Open your browser.
• Enter the EC2 public IP address.
• You should see your static website live!
________________________________________

Important Commands

Update packages	: sudo apt update
Install Apache2	: sudo apt install apache2 -y
Copy website files : sudo cp -r <files> /var/www/html/
Start Apache service : sudo systemctl start apache2
Enable Apache at boot : sudo systemctl enable apache2
________________________________________

Notes
• Make sure your files have proper permissions if needed.
• To host a secure (HTTPS) website, consider setting up an SSL certificate (e.g., Let's Encrypt).
