pipeline {
    agent any
      

    stages {
        stage('Git checkout') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/Mohd-Obaid/Trading-UI.git'
                   }
}
        stage('Install npm prerequisites'){
            steps{
                sh 'curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash'
               // Source nvm and set up environment variables
                sh 'export NVM_DIR="/var/lib/jenkins/.nvm"'
                sh '[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"'
                sh 'source ~/.bashrc'
                sh 'nvm install node'
                sh 'nvm use node'
                sh'npm audit fix'
                sh'npm install'
                sh'npm run build'
                sh'cd /var/lib/jenkins/workspace/Trading-ui-pipeline/build'
                sh'pm2 --name Trading-UI start npm -- start'
            }
        }
    }
}
