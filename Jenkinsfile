#!/usr/bin/env groovy
 
node("big-machine"){
    stage("Git Clone"){
        checkout([$class: 'GitSCM',
             branches: [[name: '*/feature-1']],
             userRemoteConfigs: [[url: 'https://github.com/SathishkumarDemoProject1/Devops-demo.git']]])
    }

   stage ("building package with docker mvn") {
      def mvnImage = docker.image('maven:3.5.4-jdk-11');
      sh "mvn clean install"
   }

    def mvn = tool "mavenV3.8.6"
    sh "echo Building java project"
    stage("Building java project"){
     sh "${mvn}/bin/mvn clean install"
    }
 stage("Code Quality check"){
    withSonarQubeEnv("DEMO_SONAR") {
      sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=devops"
    }
    sleep(20)
    timeout(time: 1, unit: 'MINUTES') {
         sh "echo Checking sonar status"
         waitForQualityGate abortPipeline: true 
    }
 }

}
