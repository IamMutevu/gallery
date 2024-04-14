pipeline{
    agent any 
    tools{
        nodejs 'npm'
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
                sh 'npm install' 
                echo 'Building the application...'
                sh 'npm run build'
            }
        }
    }
}
