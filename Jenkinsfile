pipeline{
    agent any
    stages{
        stage("Clone Code"){
            steps{
                git branch: 'master', url: 'https://github.com/IamMutevu/gallery.git'
            }
        }
        stage("Install Node.js") {
            steps {
                sh 'curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -'
                sh 'apt-get install -y nodejs'
            }
        }
        stage("Build Code"){
            steps{
                sh 'npm install'
            }
        }
    }
}