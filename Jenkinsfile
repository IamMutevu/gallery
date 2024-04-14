pipeline{
    agent none  // No global agent defined
    stages{
        stage("Clone Code"){
            agent any  // This can run on any agent
            steps{
                git branch: 'master', url: 'https://github.com/IamMutevu/gallery.git'
            }
        }
        stage("Prepare and Build Code") {
            agent {
                docker {
                    image 'node:7.4'  // Using a specific Node.js version
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
