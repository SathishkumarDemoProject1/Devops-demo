#!/usr/bin/env groovy
 
node(){
    stage("Git Clone"){
        checkout([$class: 'GitSCM',
             branches: [[name: '*/feature-1']],
             userRemoteConfigs: [[url: 'https://github.com/SathishkumarDemoProject1/Devops-demo.git']]])
    }
    def mvn = tool "mavenV3.8.6"
    sh "echo Building java project"
    stage("Building java project"){
     sh "${mvn}/bin/mvn clean install"
    }
}
