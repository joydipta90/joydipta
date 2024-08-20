# Install Jenkins on Raspberry Pi

## 1. Prepare Your Raspberry Pi
- **Power Up**: Connect your Raspberry Pi to a power source, monitor, keyboard, and mouse.
- **Boot Up**: Boot the Raspberry Pi with Raspbian (or any Debian-based OS) installed.
- **Connect to the Internet**: Ensure your Raspberry Pi is connected to the internet via Wi-Fi or Ethernet.

## 2. Update Your Raspberry Pi
Open the terminal and run the following commands to update your system:

```bash
sudo apt update
sudo apt upgrade -y
```

## 3. Create the Shell Script
In the terminal, create a new shell script file using nano or any text editor:

```bash
nano install_jenkins.sh
```

Copy and paste the following script into the editor:

```bash
#!/bin/bash

sudo apt update
sudo apt upgrade -y
sudo apt install openjdk-8-jdk -y
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update
sudo apt install jenkins -y
```

Save the file by pressing Ctrl + X, then Y, and hit Enter.

## 4. Make the Script Executable
Before running the script, make it executable:

```bash
chmod +x install_jenkins.sh
```

## 5. Run the Script
Execute the script by running the following command:

```bash
./install_jenkins.sh
```

The script will update the package lists, upgrade installed packages, install OpenJDK 8, add the Jenkins repository key, and finally install Jenkins.

## 6. Start and Enable Jenkins
After installation, start Jenkins:

```bash
sudo systemctl start jenkins
```

Enable Jenkins to start on boot:

```bash
sudo systemctl enable jenkins
```

## 7. Access Jenkins
By default, Jenkins runs on port 8080. Open a web browser on your Raspberry Pi or another device on the same network and navigate to:

```bash
http://<your_raspberry_pi_ip>:8080
```

You can find your Raspberry Pi’s IP address by running:

```bash
hostname -I
```

Follow the on-screen instructions to unlock Jenkins using the password found in the 
`file /var/lib/jenkins/secrets/initialAdminPassword`.

## 8. Secure Jenkins (Optional but Recommended)
After setting up Jenkins, it is advisable to secure it by creating an admin user and setting up security options within the Jenkins interface.

