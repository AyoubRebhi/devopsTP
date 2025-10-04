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
                sh 'mvn clean install'
            }
        }

        stage('Verify') {
            steps {
                echo '✅ everything is good'
            }
        }
    }
}
