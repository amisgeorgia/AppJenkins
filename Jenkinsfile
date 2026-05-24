pipeline {
    agent any
    
    tools {
        maven 'Maven-3.9'
    }
    
    stages {
        stage('Git Checkout') {
            steps {
                bat 'git config --global http.sslVerify false'
                git credentialsId: 'github-credentials',
                    url: 'https://github.com/amisgeorgia/AppJenkins.git',
                    branch: 'master'
            }
        }
        
        stage('Build') {
            steps {
                bat 'mvn clean install'
            }
        }
        
        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline terminé avec succès !'
        }
        failure {
            echo 'Le pipeline a échoué !'
        }
    }
}