pipeline {
    agent any

    environment {
        // Define your GitHub Personal Access Token as a secret credential
        GITHUB_TOKEN = credentials('shtoken')
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Checkout the code from your private Git repository
                    checkout([$class: 'GitSCM', 
                        branches: [[name: '*/master']],  // Specify the branch
                        userRemoteConfigs: [[url: 'https://github.com/Shraddhaw4/testrepo.git',
                                            credentialsId: GITHUB_TOKEN]]
                    ])
                }
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
