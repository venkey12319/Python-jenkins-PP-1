# Python-jenkins-PP-1

Building a Jenkins Pipeline with Docker and Docker Hub

In this post, I'll guide you through creating a Jenkins pipeline that utilizes Docker to build and store a Python application image on Docker Hub.

Prerequisites:
An EC2 instance with Ubuntu (minimum 2 CPU cores and 4 GB RAM)
A public Git repository containing:
Dockerfile
Jenkinsfile
requirements.txt
app.py (assuming your Python application)

My Public Git Repository: (https://lnkd.in/gP7Bcii5)

Steps:
Install Java:

-sudo apt update
-sudo apt install openjdk-11-jdk

Install Jenkins:
Follow the official instructions to add the Jenkins repository and install the package: 
Use code with caution Or you will get from Jenkins official document
(command: 
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
 https://lnkd.in/ghm3cX6c
 echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
 https://lnkd.in/gquwe8G5 binary/ | sudo tee \
 /etc/apt/sources.list.d/jenkins.list > /dev/null
 sudo apt-get update
sudo apt-get install jenkins)

Log in to Jenkins:
Open your browser and navigate to Ex: http://100.29.7.224:8080/. 

Use the initial password displayed by running:

-sudo cat /var/lib/jenkins/secrets/initialAdminPassword

Create a Jenkins Account:
Fill in the required details and save your credentials. Install recommended plugins.

Update Plugins:
Go to "Manage Jenkins" -> "Manage Plugins" and install:
Docker Pipeline Plugin
Git Plugin

Restart Jenkins:
Navigate to https://lnkd.in/geMUCf5c to ensure proper plugin functionality.

Save Credentials:
Go to "Manage Jenkins" -> "Credentials" and add credentials for Docker Hub and Git using "Username with password". Remember the IDs for later use.

Install Docker Via CLI:

-sudo apt install docker.io

Create a Job:
*In Jenkins, create a new item and select "Pipeline".
*Choose "Git" under SCM (source code management).
*Enter your Git repository URL and credentials.
*Specify the branch (e.g., main or master).
*Define the script path (found in your Git repository).
*Save and apply the configuration.
*Click "Build Now".

Output:
The pipeline should successfully build and display the results in the console output. You can then verify the pushed image on your Docker Hub account.

If you paste your public IP address you can see Hello World before pushing the image to Dockerhub.

Troubleshooting:
I encountered and resolved three issues during the process. Remember, errors are valuable learning experiences that help us grow!

Feel free to reach out if you have any questions or face difficulties!

Additional Notes:
Consider replacing <your_ec2_public_ip> with your EC2 instance's public IP address.
This guide assumes basic familiarity with Git and Docker concepts.
Following these steps, you'll have a functional Jenkins pipeline to build and store your Python application image on Docker Hub. The output is accessible on Docker Hub (public). (https://lnkd.in/gr-Q5QUr)
