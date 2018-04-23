properties([pipelineTriggers([githubPush()])])

node('linux') {
    git url: 'https://github.com/giddo4all/infrastructure-pipeline.git', branch: 'master'
    stage('Test') {
        sh "env"
    }
}
