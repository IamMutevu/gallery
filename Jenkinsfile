pipeline{
    agent none 
    stages{
        stage("Clone Code"){
            agent any 
            steps{
                git branch: 'master', url: 'https://github.com/IamMutevu/gallery.git'
            }
        }
        stage("Prepare and Build Code") {
            agent {
                docker {
                    image 'node:16-alpine' 
                    args '-v /home/jenkins/.npm:/root/.npm' 
                }
            }
            steps {
                withNPM(npmrcConfig:'my-custom-npmrc') {
                    echo "Installing dependencies..."
                    sh 'npm install'
                    echo "Performing npm build..."
                    sh 'npm run build'  // Assuming there's a build script in package.json
                }
            }
        }
    }
}
