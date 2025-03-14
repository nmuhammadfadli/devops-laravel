pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    docker.image('shippingdocker/php-composer:8.4').inside('-u root') {
                        sh 'rm -f composer.lock'
                        sh 'composer install'
                    }
                }
            }
        }

        stage('Testing') {
            steps {
                script {
                    docker.image('ubuntu:latest').inside('-u root') {
                        sh 'echo "Ini adalah test"'
                    }
                }
            }
        }
    }
}
