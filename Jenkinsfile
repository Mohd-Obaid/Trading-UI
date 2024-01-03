pipeline {
    agent any
      

    stages {
        stage('Git checkout') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/betawins/Trading-UI.git'
                   }
        }
        stage('Install Node.js and npm') {
            steps {
            sh 'yum install -y nodejs npm'  // This command depends on your system's package manager
        }
        }

        stage('Install npm prerequisites'){
            steps{
                sh'npm audit fix'
                sh'npm install'
                sh'npm run build'
                sh'cd /var/lib/jenkins/workspace/Trading-ui-pipeline/build'
                sh'pm2 --name Trading-UI start npm -- start'
            }
        }
    }
}
