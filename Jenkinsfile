pipeline{
    agent any
    stages{
        stage("Clone Code"){
            steps{
                git branch: 'master', url: 'https://github.com/IamMutevu/gallery.git'
            }
        }
        stage("Build Code"){
            steps{
                sh 'npm install'
            }
        }
    }
}