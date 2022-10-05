#!/usr/bin/env groovy
 
node(){
    stage("Git Clone"){
        checkout([$class: 'GitSCM',
             branches: [[name: '*/feature-1']],
             userRemoteConfigs: [[url: 'https://github.com/SathishkumarDemoProject1/Devops-demo.git']]])
    }
    stage("Updating path"){
        sh "export PATH=/home/ec2-user/jenkins-ssh/apache-maven-3.8.6/bin:$PATH"
    }
    sh "echo Building java project"
    stage("Building java project"){
        sh "/home/ec2-user/jenkins-ssh/apache-maven-3.8.6/bin/mvn clean install"
    }
}
