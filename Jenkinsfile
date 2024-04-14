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
                sh 'npm install' 
                // sh 'node server'
            }
        }
    }
    post {
        always {
            slackSend (
                channel: env.SLACK_CHANNEL, 
                color: '#FFFF00', 
                message: "Build ${env.BUILD_NUMBER} completed"
            )
        }
    }
}
