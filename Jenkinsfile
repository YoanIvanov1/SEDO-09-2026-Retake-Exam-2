pipeline {
    agent any

    environment {
        DOTNET_ROLL_FORWARD = 'Major'
    }

    triggers {
        pollSCM('* * * * *')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Restore dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage('Run tests') {
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}