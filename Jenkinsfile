properties([pipelineTriggers([githubPush()])])

node('linux') {
    git url: 'https://github.com/giddo4all/infrastructure-pipeline.git', branch: 'master'
    try {
    stage('Test') {
        sh "env"
    }
    stage ("GetInstances") {

    sh "aws ec2 describe-instances --region us-east-1"
}

stage ("CreateInstance") {
    sh "aws ec2 run-instances --image-id ami-287dnf7 --count 1 --instance-type t2.micro --key-name seis665 --security-group-ids sg-9eef97d7 --subnet-id subnet-ba5cb9e6 --region us-east-1"
} catch (Exception e) {
  currentBuild.result = 'FAILURE'   
} finally {
    echo pwd()
    slackSend('#00FFFF' : colorCode, baseUrl : 'https://seis-602-pos-project.slack.com/services/hooks/jenkins-ci/', tokenCredentialId: 'kiwbZmTVIMmWlQUBmay6Ainb', channel: '#symtest', message: "Sent slack message")
}
        
    
}
