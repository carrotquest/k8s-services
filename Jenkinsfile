pipeline {
    agent any
//     {
//         node { label 'some label' }
//     }

    environment {
        SOME_VARIABLE = "one"
    }

    stages {
        stage('Checkout'){
            steps{
                checkout()
            }
        }

        stage('Build Helm chart') {
            steps {
                ansiColor('xterm') { sh "helm package cqapi-env --version 0.1.${BUILD_NUMBER}" }
            }
        }

        stage('Push Helm chart') {
            steps {
                ansiColor('xterm') { sh "helm push cqapi-env-0.1.${BUILD_NUMBER}.tgz carrotquest" }
            }
        }
    } //stages

} //pipeline
