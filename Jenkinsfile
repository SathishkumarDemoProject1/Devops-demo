#!/usr/bin/env groovy
 
node(){
    stage("Git Clone"){
        checkout([$class: 'GitSCM',
             branches: [[name: '*/feature-1']],
             userRemoteConfigs: [[url: 'https://github.com/SathishkumarDemoProject1/Devops-demo.git']]])
    }
   stage ("building package with docker mvn") {
//       def mvnImage = docker.image('maven:3.5.4-jdk-11');
//       withSonarQubeEnv("DEMO_SONAR") {
//          mvnImage.inside(){
//             sh "mvn clean install"
//             sh "mvn clean verify sonar:sonar -Dsonar.projectKey=devops"
//          }
//       }
   }
 stage ("SONAR CHECK") {
//     sleep(20)
//     timeout(time: 1, unit: 'MINUTES') {
//          sh "echo Checking sonar status"
//          waitForQualityGate abortPipeline: true 
//     }
 }
 stage ("build docker image") {
  sh "docker build -t sathishkumar281995/devops-demo-image ."
 }
 
  stage ("push docker image") {
   withCredentials([string(credentialsId: 'docker_password', variable: 'PASSWORD')]) {
    sh "docker login -u sathishkumar281995 -p $PASSWORD"
    sh "docker push sathishkumar281995/devops-demo-image:latest"
   }
 }

}
