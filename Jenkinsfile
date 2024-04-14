pipeline{
    agent any
    stages{
        stage("Clone Code"){
            steps{
                git branch: 'master', url: 'https://github.com/IamMutevu/gallery.git'
            }
        }
        stage("Install Node.js") {
            agent {
                docker {
                    image 'node:7.4'
                }
            }
            steps {
                withNPM(npmrcConfig:'my-custom-npmrc') {
                    echo "Performing npm build..."
                    sh 'npm install'
                }
            }
        }
        stage("Build Code"){
            steps{
                sh 'npm install'
            }
        }
    }
}