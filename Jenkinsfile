pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                sh 'mkdir -p build'
                sh 'cp index.html build/'
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'build/**', fingerprint: true
            }
        }
        stage('Notify') {
            steps {
                emailext (
                    subject: "Jenkins Job: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                    body: "Build completed.\nStatus: ${currentBuild.currentResult}\nCheck console: ${env.BUILD_URL}",
                    to: 'aishawon.info@gmail.com'
                )
            }
        }
    }
}
