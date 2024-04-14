pipeline{
    agent any 
    stages{
        stage("Clone Code"){
            steps{
                git branch: 'master', url: 'https://github.com/IamMutevu/gallery.git'
            }
        }
        stage("Prepare and Build Code") {
            agent {
                any {
                    image 'node:16-alpine' 
                    args '-v /home/jenkins/.npm:/root/.npm' 
                }
            }
            steps {
                echo 'Installing dependencies...'
                sh 'npm install' // Install all dependencies
                echo 'Building the application...'
                sh 'npm run build' // Run the build script specified in package.json
            }
        }
    }
}
