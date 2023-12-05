pipeline {
    agent {label 'packer'}
    parameters {
        string(defaultValue: "", description: 'K', name: 'test')
    }
    stages {
        stage('Checkout') {
            steps {
                script {
                    // Checkout the code from your private Git repository
                    git "https://github.com/Shraddhaw4/testrepo.git"
                }
            }
        }

        stage('PrintParameter'){
            steps{
                sh 'echo ${HELLO}'
            }
        }

        stage('Build') {
            steps {
                // Activate a virtual environment (if needed)
                sh 'python -m venv venv'
                sh 'source venv/bin/activate'
              
                // Build the Python script
                sh 'python hello.py'
            }
        }
    }

    post {
        success {
            // This block is executed when the build is successful
            echo 'Build successful!'
        }
        failure {
            // This block is executed when the build fails
            echo 'Build failed!'
        }
    }
}
