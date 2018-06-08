#!/usr/bin/env groovy

pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/ravikiranmaroju/java-code.git']]])
            }
        }
        stage('build') {
            steps {
                sh 'mvn package'
            }
        }
        stage('push') {
            steps {
                sh '''curl -u admin:admin -T target/grants.war "http://ec2-18-188-120-206.us-east-2.compute.amazonaws.com:8081/artifactory/articatory-jenkins/grants.war"'''
            }
        }
           }
        }
        stage('deploy') {
            steps {
                sh '''sudo apt update -y
                   sudo apt install tomcat8 tomcat8-admin tomcat8-user -y
                     cd /var/lib/tomcat8/webapps
                      sudo chmod 777 /var/lib/tomcat8/webapps
                        sudo chmod 777 /etc/tomcat8/tomcat-users.xml
                          curl -u admin:admin -O "http://ec2-18-218-164-124.us-east-2.compute.amazonaws.com:8081/artifactory/articatory-jenkins/grants.war"'''
            }
        }
    }
}
