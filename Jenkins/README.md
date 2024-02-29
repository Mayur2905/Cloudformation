Creating A Jenkins pipeline for hosting a student app

Code:
```
pipeline{
    agent {
	label ‘agent1’
	}
    stages{
        stage('Pull a file from git')
        {
            steps{
                sh 'git clone https://github.com/Mayur2905/webapp.git'
            }
        }
        stage('Installing Apache2')
        {
            steps{
                sh "sudo  apt-get update"
                sh "sudo  apt-get install apache2 -y"
                sh "sudo  systemctl start apache2"
            }
        }
        stage('Downloading Tomcat 8')
        {
            steps{
                sh 'sudo wget https://dlcdn.apache.org/tomcat/tomcat-8/v8.5.99/bin/apache-tomcat-8.5.99.tar.gz'
                sh 'sudo tar -xvf apache-tomcat-8.5.99.tar.gz'
            }
        }
        stage('Deploying war file')
        {
            steps{
                sh "sudo  mv -r webapp/student.war apache-tomcat-8.5.99/webapps"
            }
        }
        stage('Starting Apache 8')
        {
            steps{
                sh 'sudo ./apache-tomcat-8.5.99/bin/catalina.sh start'
            }
        }
    }
}

```


Code Overview:
Overview
This pipeline is designed to pull a file from a Git repository, install Apache2, download and extract Apache Tomcat 8, deploy a WAR file to Tomcat, and start Apache Tomcat 8.
Pipeline Structure
Agent: The pipeline is configured to run on any available agent.
Stages: The pipeline consists of several stages, each representing a distinct phase of the deployment process.
Stages
Pull a file from git
This stage clones the webapp repository (https://github.com/Mayur2905/webapp.git).
Installing Apache2
This stage installs Apache2 web server by updating the package list, installing Apache2, and starting the Apache2 service.
Downloading Tomcat 8
This stage downloads Apache Tomcat 8.5.99 from the official Apache website and extracts the downloaded archive.
Deploying war file
This stage moves the student.war file from the cloned webapp repository to the webapps directory of Apache Tomcat 8.5.99, effectively deploying the WAR file.
Starting Apache Tomcat 8
This stage starts Apache Tomcat 8.5.99 using the catalina.sh script.


Output:

