pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
     stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/AyoubRebhi/devopsTP.git'
            }
        }

        stage('Build') {
            steps {
                dir('TP-Projet') { // Adjust this to match your actual folder
                    sh 'mvn clean package -DskipTests'                }
            }
        }
         stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQubeLocal') { // Match the name you configured in Jenkins
                    dir('TP-Projet') {
                        sh 'sonar-scanner'
                    }
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
        stage('Verify') {
            steps {
                echo '✅ everything is good'
            }
        }
    }
}
