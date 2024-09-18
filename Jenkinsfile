pipeline {
    agent { docker { image 'node:16' } }
    stages {
        stage('Install dependencies') {
            steps {
                sh 'node --version'
                sh 'npm --version'
                sh 'npm install --save'
            }
        }
        stage('Snyk Scan') {
            steps {
                echo 'Scanning...'
                sh '''
                npm install snyk -g
                snyk auth ${SNYK_TOKEN}  
                snyk test --severity-threshold=high
                '''
            }
        }
    }
}