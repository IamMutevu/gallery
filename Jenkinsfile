pipeline{
    agent any 
    tools{
        npm 'npm'
    }
    stages{
        stage("Clone Code"){
            steps{
                git branch: 'master', url: 'https://github.com/IamMutevu/gallery.git'
            }
        }
        stage("Prepare and Build Code") {
            steps {
                echo 'Installing dependencies...'
                sh 'npm install' // Install all dependencies
                echo 'Building the application...'
                sh 'npm run build' // Run the build script specified in package.json
            }
        }
    }
}
