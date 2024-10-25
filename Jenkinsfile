pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Install Dependencies') {
            steps {
                bat 'composer install --no-interaction --ignore-platform-req=ext-fileinfo'
            }
        }
        
        stage('Prepare Laravel') {
            steps {
                bat 'copy .env.example .env'
                bat 'php artisan key:generate'
            }
        }
        
        stage('Run Tests') {
            steps {
                bat 'php artisan test'
            }
        }
        
        stage('Build') {
            steps {
                bat 'php artisan config:cache'
                bat 'php artisan route:cache'
                echo 'Build completed'
            }
        }
    }
}