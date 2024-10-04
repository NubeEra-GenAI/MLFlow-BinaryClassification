pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/NubeEra-GenAI/MLFlow-BinaryClassification.git'
            }
        }
        stage('Run Project') {
            steps {
                script {
                    //Define Variable for Environment name
                    def venvDir ='venv'
                    
                    // Create Virtual Env.
                    //   virtualenv .env
                    //   python -m virtualenv .env
                    //   python -m venv .env
                    sh "python3 -m virtualenv ${venvDir}"
                    //Type of Shell = BASH 
                    // sh "source ${venvDir}/bin/activate"
                    //  OR
                    // //Type of Shell = SH/BASH
                    sh ". ${venvDir}/bin/activate"
                    //  OR
                    // Type of Shell = SH --> BASH
                    //sh "bash -c 'source ${venvDir}/bin/activate'"
                    
                    sh """
                        pip install -r requirements.txt 
                        python ml_binary_classification.py
                    """
                }
            }
        }
    }
    post {
        always {
            // Clean up Virtual Env.
            sh "rm -rf venv"
        }
    }
}
