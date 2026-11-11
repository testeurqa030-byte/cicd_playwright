 pipeline {
    agent {
        docker{
            image 'mcr.microsoft.com/playwright:v1.65.0-jammy'
            args '-u root --entrypoint='
        }
    }

    parameters {
        booleanParam(name: 'isBrowser', defaultValue: true, description: 'lancer avec tous les browsers ?')
        choice(name: 'rouaa', choices: ['chromium', 'firefox', 'webkit'], description: 'Choisir un browser ?')

     }
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
                script{
                    if(params.isBrowser == true){
                        sh "npx playwright test"
                    }else {
                        sh "npx playwright test --project=${params.rouaa}"
                    }
                }
            }
        }
       
         
    }
}
