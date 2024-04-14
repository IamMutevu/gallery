pipeline{
    agent any 
    environment {
        HEROKU_API_KEY = credentials('heroku-api-key')
        HEROKU_APP_NAME = 'devops-ip1'
        HEROKU_APP_URL = 'https://devops-ip1-f1da9419f34e.herokuapp.com/'
    }
    tools{
        nodejs 'npm'
    }
    stages{
        stage("Build") {
            steps {
                echo "Cloning code..."
                git branch: 'master', url: 'https://github.com/IamMutevu/gallery.git'
                echo "Building code..."
                sh 'npm install' 
            }
        }
        stage("Test") {
            steps {
                echo "Testing code..."
                sh 'npm test' 
            }
            post {
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
        stage("Deploy") {
           steps {
                script {
                    sh "git remote add heroku https://git.heroku.com/${HEROKU_APP_NAME}.git"
                    sh "git push heroku master"
                }
            }
            post {
                success {
                    slackSend (
                        channel: env.SLACK_CHANNEL, 
                        color: '#FFFF00', 
                        message: "Build ${env.BUILD_NUMBER} completed. View the site here: ${HEROKU_APP_URL}"
                    )
                }
            }
        }
    }
}
