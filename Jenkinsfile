pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
               git branch: 'main', url: 'https://github.com/AyoubRebhi/devopsTP.git' 
            }
        }

        stage('Build') {
    steps {
        sh '''
            echo "🔧 Starting build..."
            mkdir -p build
            echo "Build complete!" > build/status.txt
        '''
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
