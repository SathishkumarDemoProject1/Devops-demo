#!/usr/bin/env groovy

node("pipeline"){
    sh "export PATH=/root/apache-maven-3.8.6/bin:$PATH"
    sh "echo Building java project"
    sh "/root/apache-maven-3.8.6/bin/mvn clean install"
}
