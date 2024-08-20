<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Install Jenkins on Raspberry Pi</title>
</head>
<body>
    <h1>Install Jenkins on Raspberry Pi</h1>

    <h2>1. Prepare Your Raspberry Pi</h2>
    <ul>
        <li><strong>Power Up:</strong> Connect your Raspberry Pi to a power source, monitor, keyboard, and mouse.</li>
        <li><strong>Boot Up:</strong> Boot the Raspberry Pi with Raspbian (or any Debian-based OS) installed.</li>
        <li><strong>Connect to the Internet:</strong> Ensure your Raspberry Pi is connected to the internet via Wi-Fi or Ethernet.</li>
    </ul>

    <h2>2. Update Your Raspberry Pi</h2>
    <p>Open the terminal and run the following commands to update your system:</p>
    <pre><code>sudo apt update
sudo apt upgrade -y
    </code></pre>
    <p>This ensures that all packages on your Raspberry Pi are up to date.</p>

    <h2>3. Create the Shell Script</h2>
    <p>In the terminal, create a new shell script file using <code>nano</code> or any text editor:</p>
    <pre><code>nano install_jenkins.sh
    </code></pre>
    <p>Copy and paste the following script into the editor:</p>
    <pre><code>#!/bin/bash

sudo apt update
sudo apt upgrade -y
sudo apt install openjdk-8-jdk -y
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update
sudo apt install jenkins -y
    </code></pre>
    <p>Save the file by pressing <code>Ctrl + X</code>, then <code>Y</code>, and hit <code>Enter</code>.</p>

    <h2>4. Make the Script Executable</h2>
    <p>Before running the script, make it executable:</p>
    <pre><code>chmod +x install_jenkins.sh
    </code></pre>

    <h2>5. Run the Script</h2>
    <p>Execute the script by running the following command:</p>
    <pre><code>./install_jenkins.sh
    </code></pre>
    <p>The script will update the package lists, upgrade installed packages, install OpenJDK 8, add the Jenkins repository key, and finally install Jenkins.</p>

    <h2>6. Start and Enable Jenkins</h2>
    <p>After installation, start Jenkins:</p>
    <pre><code>sudo systemctl start jenkins
    </code></pre>
    <p>Enable Jenkins to start on boot:</p>
    <pre><code>sudo systemctl enable jenkins
    </code></pre>

    <h2>7. Access Jenkins</h2>
    <p>By default, Jenkins runs on port 8080. Open a web browser on your Raspberry Pi or another device on the same network and navigate to:</p>
    <pre><code>http://&lt;your_raspberry_pi_ip&gt;:8080
    </code></pre>
    <p>You can find your Raspberry Pi’s IP address by running:</p>
    <pre><code>hostname -I
    </code></pre>
    <p>Follow the on-screen instructions to unlock Jenkins using the password found in the file <code>/var/lib/jenkins/secrets/initialAdminPassword</code>.</p>

    <h2>8. Secure Jenkins (Optional but Recommended)</h2>
    <p>After setting up Jenkins, it is advisable to secure it by creating an admin user and setting up security options within the Jenkins interface.</p>
</body>
</html>
