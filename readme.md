# Creating and Managing an AWS EC2 Instance with Ubuntu Server

This is a step-by-step process on how to launch an AWS EC2 instance running Ubuntu Server. connect to it using SSH, install the `tree` package, and Stop the instance. 

## Prerequisites
- **AWS Account**: Access to the AWS Management Console.
- **Key Pair**: An existing key pair.
- **SSH Client**: Terminal (Linux/Mac) or PuTTY, MobaXterm (Windows).


## Creating an AWS EC2 Instance

### Step 1: Log in to the AWS Management Console
1. Navigate to [AWS Management Console](https://aws.amazon.com/console/).
2. Sign in and go to the **EC2 Dashboard**.


<video src="videos/vid1.mp4" controls width="600"></video>

### Step 2: Launch a New EC2 Instance
1. Click **Launch Instance** > **Launch Instance**.
2. Name: `Ubuntu-server`.
3. AMI: **Ubuntu Server 22.04 LTS**.
4. Instance Type: `t2.micro`.
5. Key Pair: Select `my-key-pair`.
6. Network: Click Edit.
- VPC: Use the default VPC.
- Subnet: Choose a public subnet (e.g., us-east-1a).
- Auto-assign public IP: Enable.
- Security Group: Create a new security group and add rules: HTTP: Port 80, Source: Anywhere (0.0.0.0/0). SSH: Port 22, Source: anywhere (0.0.0.0/0).

7. Storage: 8 GiB gp2.
8. Click **Launch Instance**.


<video src="videos/vid2.mp4" controls width="600"></video>

### Step 3: Verify Instance Status
1. Go to **Instances** in the EC2 Dashboard.
2. Confirm the instance is **Running**.
3. Note the **Public IPv4 Address**.


<video src="videos/vid3.mp4" controls width="600"></video>

### Step 4: Connect to the EC2 Instance via SSH
1. Set key pair permissions: `chmod 400 my-key-pair.pem`.
2. SSH: `ssh -i my-key-pair.pem ubuntu@<Public-IP>`.
3. Accept the host key if prompted.


<video src="videos/vid4.mp4" controls width="600"></video>

### Step 5: Install the `tree` Package
1. Update packages: `sudo apt update`.
2. Install `tree`: `sudo apt install tree -y`.
3. Verify: `tree --version`.
4. Test: `tree /home/ubuntu`.


<video src="videos/vid5.mp4" controls width="600"></video>

### Step 6: Uninstall the `tree` Package
1. Remove: `sudo apt remove tree -y`.
2. Clean up: `sudo apt autoremove -y`.
3. Verify: `tree --version` (should fail).


<video src="videos/vid6.mp4" controls width="600"></video>

### Step 7: Stop the EC2 Instance
1. Go to **Instances**, select the instance.
2. Click **Instance State** > **Stop Instance**.
3. Confirm and verify it's in **Stop** state.

<video src="videos/vid7.mp4" controls width="600"></video>

#
