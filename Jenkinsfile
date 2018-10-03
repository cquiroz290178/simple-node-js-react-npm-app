pipeline {
    agent {
        docker {
            image 'node:6-alpine' 
            args '-p 3003:3000' 
        }
    }
    environment {
            CI='true'
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
        stage('test') { 
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Terminar Usando el Sitio Web ? (Click "Proceder" to continuar)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
    
}

