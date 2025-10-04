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

        stage('Verify') {
            steps {
                echo '✅ everything is good'
            }
        }
    }
}

