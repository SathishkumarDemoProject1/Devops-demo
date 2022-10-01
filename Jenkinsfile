#!/usr/bin/env groovy

node("pipeline"){
    checkout([$class: 'GitSCM',
         branches: [[name: '*/feature-1']],
         userRemoteConfigs: [[url: 'https://github.com/SathishkumarDemoProject1/Devops-demo.git']]])
    
    sh "export PATH=/home/ec2-user/jenkins-ssh/apache-maven-3.8.6/bin:$PATH"
    sh "echo Building java project"
    sh "mvn clean install"
}
