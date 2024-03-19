pipeline {
    agent {label 'packer'}
    environment {
        #user_name = env.BUILD_USER
    }
    parameters {
        string(defaultValue: "", description: 'K', name: 'test')
        extendedChoice name: 'states', description: 'Choose one state', defaultValue: 'mah', type: 'PT_RADIO', descriptionPropertyValue: 'Maharashtra,Gujarat,Dehradun', value: 'mah,guj,deh'
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
                sh 'echo ${states}'
                sh 'echo ${test}'
                sh 'echo ${BUILD_USER}'
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
