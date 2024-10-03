pipeline {
    agent any

    environment {
        NODEJS_HOME = tool name: 'NodeJS', type: 'NodeJSInstallation'
        PATH = "${NODEJS_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Tamizhenthan/sampleDevOps.git'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                // Add your test command here, e.g., npm test
                echo 'Running Tests...'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'npm run build' // If your project has a build step
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                sh 'scp -r ./ ubuntu@3.110.190.34:/var/lib/jenkins'
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
