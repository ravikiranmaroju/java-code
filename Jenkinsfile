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
                echo 'pushing'
            }
        }
        stage('deploy') {
            steps {
                echo 'deploying'
            }
        }
    }
}
