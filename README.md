
# LAMP Stack Deployment on AWS EC2 Instance

This README provides instructions to create an AWS EC2 instance, configure a LAMP environment, and deploy sample PHP code. Follow these steps carefully to complete the assignment.


## STEP 1: Launch an EC2 t2.micro Instance

- Log in to the AWS Management Console.

- Navigate to EC2 under the "Compute" section.

-  Click Launch Instances and configure as follows:

    - Name: LAMP-Server

    - AMI: Amazon Linux 2 (Free Tier eligible)

    - Instance Type: t2.micro

    - Key Pair: Create or use an existing key pair.

    - Security Group: Allow HTTP (port 80) and SSH (port 22) traffic.

- Click Launch Instance and wait for it to initialize.


## Step 2: Connect to the EC2 Instance

- Go to the EC2 dashboard, find your instance, and copy the Public IP Address.

- Open your terminal or SSH client (e.g., MobaXterm) and connect using:

```bash
  ssh -i "your-key.pem" ec2-user@<Public-IP-Address>
```
## Step 3: Configure the LAMP Environment

- Install Apache
```bash
sudo yum update -y
sudo yum install -y httpd
sudo systemctl start httpd
sudo systemctl enable httpd
```
- Install PHP
```
sudo amazon-linux-extras enable php8.0
sudo yum install -y php php-mysqlnd
sudo systemctl restart httpd
```
- Install MySQL Client
```
sudo yum install -y mariadb
```
## Step 4: Deploy Sample PHP Code

- Navigate to the web root directory:

``` 
 cd /var/www/html 
```

- Create a sample PHP file:

```
 sudo nano index.php
```

- Add the following code:
```
<?php
echo "Hello, LAMP server is running!";
?>
```
- Save and exit (Ctrl + O, Enter, Ctrl + X).
    
## Step 5: Test the Deployment

- Open your browser and access the server using:
```
  http://<Public-IP-Address>
```

- You should see the message:

```bash
  Hello, LAMP server is running!
```


