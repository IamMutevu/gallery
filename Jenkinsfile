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
        failure {
            emailext (
                subject: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                body: """<p>FAILURE!</p>
                         <p>Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' failed.</p>
                         <p>Check console output at '<a href="${env.BUILD_URL}">Build URL</a>'</p>""",
                to: 'ian.mutevu@student.moringaschool.com',
                mimeType: 'text/html'
            )
        }
    }
}
