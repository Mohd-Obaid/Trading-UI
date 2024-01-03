pipeline {
    agent any

    environment {
        NVM_DIR = '/var/lib/jenkins/.nvm'
        PATH = "${NVM_DIR}/current/bin:${PATH}"
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
                    // Install nvm
                    sh 'curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash'

                    // Source nvm and set up environment variables
                    sh 'export NVM_DIR="/var/lib/jenkins/.nvm"'
                    sh '[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"'

                    // Install Node.js using nvm
                    sh 'nvm install node'
                    sh 'nvm use node'

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
