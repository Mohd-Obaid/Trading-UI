pipeline {
    agent any

    environment {
        PATH = "${tool 'Node.js'}/bin:${PATH}"
    }

    stages {
        stage('Git checkout') {
            steps {
                git 'https://github.com/Mohd-Obaid/Trading-UI.git'
            }
        }

        stage('Install npm prerequisites') {
            steps {
                script {
                    // Use the Jenkins Node.js tool installation
                    def nodeHome = tool 'Node.js'
                    env.PATH = "${nodeHome}/bin:${env.PATH}"

                    // Verify Node.js and npm installation
                    sh 'node --version'
                    sh 'npm --version'

                    // Navigate to the project directory
                    dir('path/to/your/project') {
                        // Run npm commands
                        sh 'npm audit fix'
                        sh 'npm install'
                        sh 'npm run build'
                        sh 'pm2 --name Trading-UI start npm -- start'
                    }
                }
            }
        }
    }
}
