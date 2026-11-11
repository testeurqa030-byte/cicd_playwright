pipeline {
    agent {
        docker{
            image 'mcr.microsoft.com/playwright:v1.65.0-jammy'
            args '-u root --entrypoint='
        }
    }

    triggers{  githubPush() }
    stages {
         stage('Check version nodejs') {
            steps {
                sh 'npm --version'
            }
        }
        stage('installation dependances') {
            steps {
                sh 'npm install'
            }
        }
        stage('Lancer le test') {
            steps {
                sh 'npx playwright test'
            }
        }
       
         
    }
}
