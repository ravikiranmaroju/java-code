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
                echo 'building'
            }
        }
        stage('push') {
            steps {
                sh '''curl -u admin:admin -T target/grants.war "http://ec2-18-188-120-206.us-east-2.compute.amazonaws.com:8081/artifactory/articatory-jenkins/grants.war"'''
            }
        }
        stage('deploy') {
            steps {
                echo 'deploying'
            }
        }
    }
}
