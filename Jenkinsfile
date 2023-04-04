pipeline {
    agent {
        docker {
            image 'mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019'
        }
    }
    stages {
        stage('Build') {
            steps {
                bat 'dotnet restore'
                bat 'dotnet build'
            }
        }
        stage('Test') {
            steps {
                bat 'dotnet test'
            }
        }
        stage('Publish') {
            steps {
                bat 'dotnet publish'
            }
        }
        stage('Deploy') {
            steps {
                bat 'docker build -t my-app .'
                bat 'docker run -d --name my-app-container my-app'
            }
        }
    }
}
