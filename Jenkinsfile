pipeline {
    agent any

    tools {
        sonarQube 'SonarQubeLocal'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/AyoubRebhi/devopsTP.git'
            }
        }

        stage('Build') {
            steps {
                sh './build.sh' // or your build command
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
