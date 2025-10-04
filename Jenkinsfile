pipeline {
    agent any

    environment {
        // Optional: define other env vars here
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/AyoubRebhi/devopsTP.git'
            }
        }

        stage('Build') {
            steps {
                sh './build.sh' // or your actual build command
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQubeLocal') {
                    sh 'sonar-scanner'
                }
            }
        }

        stage('Quality Gate') {
            steps {
                timeout(time: 1, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}
