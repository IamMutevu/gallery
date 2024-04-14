pipeline{
    agent any
    stages{
        stage("Clone Code"){
            steps{
                git branch: 'master', url: 'https://github.com/IamMutevu/gallery.git'
            }
        }
        stage("Install Node.js") {
            steps {
                 sh 'curl -LO https://nodejs.org/dist/v14.17.0/node-v14.17.0-linux-x64.tar.xz'
                sh 'mkdir -p $HOME/node'
                sh 'tar -xJf node-v14.17.0-linux-x64.tar.xz -C $HOME/node --strip-components=1'
                sh 'export PATH=$HOME/node/bin:$PATH'
            }
        }
        stage("Build Code"){
            steps{
                sh 'npm install'
            }
        }
    }
}