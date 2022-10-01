#!/usr/bin/env groovy

node("pipeline"){
    sh "export PATH=/home/ec2-user/jenkins-ssh/apache-maven-3.8.6/bin:$PATH"
    sh "echo Building java project"
    sh "/home/ec2-user/jenkins-ssh/apache-maven-3.8.6/bin/mvn clean install"
}
