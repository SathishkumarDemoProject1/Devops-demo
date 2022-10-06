#!/usr/bin/env groovy
 
node("big-machine"){
    stage("Git Clone"){
        checkout([$class: 'GitSCM',
             branches: [[name: '*/feature-1']],
             userRemoteConfigs: [[url: 'https://github.com/SathishkumarDemoProject1/Devops-demo.git']]])
    }
   stage ("building package with docker mvn") {
      def mvnImage = docker.image('maven:3.5.4-jdk-11');
      withSonarQubeEnv("DEMO_SONAR") {
         mvnImage.inside(){
            sh "mvn clean install"
            sh "mvn clean verify sonar:sonar -Dsonar.projectKey=devops"
         }
      }
   }
   stage ("SONAR CHECK")
    sleep(20)
    timeout(time: 1, unit: 'MINUTES') {
         sh "echo Checking sonar status"
         waitForQualityGate abortPipeline: true 
    }


}
