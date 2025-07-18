pipeline {
    agent any

    options {
        buildDiscarder(logRotator(
            daysToKeepStr: '10',
            numToKeepStr: '5',
            artifactDaysToKeepStr: '3',
            artifactNumToKeepStr: '2'
        ))
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                sh './mvnw clean'
                sh './mvnw compile test-compile'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh './mvnw test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                sh '''
                    sudo mkdir -p /var/www/jenkins/app
                    sudo rsync -avz . /var/www/jenkins/app
                '''
            }
        }
    }

    post {
        success {
            slackSend (color: '#00FF00', message: "Build Successful: ${env.JOB_NAME} #${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)")
        }
        failure {
            slackSend (color: '#FF0000', message: "Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)")
        }
    }
}