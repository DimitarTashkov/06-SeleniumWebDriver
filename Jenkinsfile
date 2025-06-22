pipeline {
    agent any

    stages {
        stage('Checkout the repository') {
            steps {
                checkout scm
            }
        }

        stage('Built the project') {
            steps {
                bat 'dotnet build'
            }
        }

        stage('Run tests in parallel'){
            parallel {
        
        stage('Project 1 tests') {
            steps {
                bat 'dotnet test TestProject1 --no-build --verbosity normal' // Runs your tests
            }

        }
        stage('Project 2 tests') {
            steps {
                bat 'dotnet test TestProject2 --no-build --verbosity normal' // Runs your tests
            }

        }
        stage('Project 3 tests') {
            steps {
                bat 'dotnet test TestProject3 --no-build --verbosity normal' // Runs your tests
            }

        }
        }

    }
    

    post {
        always {
            echo 'Pipeline completed.'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
