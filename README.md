

# 🌟 Set Up Your Own Git Server on AWS EC2 🌟

This guide will help you set up your own Git server on an AWS EC2 instance. You'll be able to create, manage, and push to repositories hosted on your EC2 instance.

## 🚀 Prerequisites

- An AWS EC2 instance running Ubuntu
- SSH access to your EC2 instance
- Basic knowledge of Git and command line operations

## 🛠️ Step-by-Step Guide

### 1. Connect to Your EC2 Instance

Connect to your EC2 instance using SSH:
```bash
ssh -i /path/to/your-key.pem ubuntu@your-ec2-instance-ip
```

### 2. Install Git

Update the package lists and install Git:
```bash
sudo apt update
sudo apt install git -y
```

### 3. Create a Bare Repository

Navigate to the directory where you want to store your repository and create a bare repository:
```bash
sudo mkdir -p /var/lib/git
cd /var/lib/git
sudo git init --bare my-project.git
```

### 4. Set Up a Git User

Create a new user for Git operations and give them the necessary permissions:
```bash
sudo adduser git
sudo usermod -aG sudo git
```

### 5. Configure SSH Access for Git User

1. Switch to the `git` user:
    ```bash
    sudo su - git
    ```

2. Set up SSH keys for the `git` user:
    ```bash
    mkdir ~/.ssh
    chmod 700 ~/.ssh
    touch ~/.ssh/authorized_keys
    chmod 600 ~/.ssh/authorized_keys
    ```

3. Add your public key to `authorized_keys`:
    ```bash
    echo "your-public-ssh-key" >> ~/.ssh/authorized_keys
    ```

### 6. Push to Your Bare Repository

On your local machine, add the remote repository and push your changes:
```bash
git remote add origin ssh://git@your-ec2-instance-ip:/var/lib/git/my-project.git
git push origin master
```

### 7. Manage Repository Access (Optional)

To manage repository access and permissions, consider setting up `git-shell` or using other tools like `Gitea` or `GitLab`.

## ✅ Conclusion

Congratulations! 🎉 You've successfully set up your own Git server on an AWS EC2 instance. You can now create, manage, and push to repositories hosted on your own server.

For any issues or questions, feel free to reach out! Happy coding! 💻🚀
