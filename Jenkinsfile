properties([pipelineTriggers([githubPush()])])
properties([parameters([choice(choices: "master\nfeature-1\nfeature-2", name: 'branch')])])
node { git url: 'https://github.com/mohamedriad/gitjenkinsintegration.git', branch:'master' }
pipeline{
  agent any
  stages{
    stage('SCM'){
      steps{
        node('slave_2'){
          git url: 'https://github.com/mohamedriad/gitjenkinsintegration', branch: "${params.branch}"
        }

      }

    }
    stage('RUN')
    {
      steps{
         node('slave_2'){
          bat 'python test.py'
        }
          
      }
    }
    stage('Slack')
    {
      steps{
        slackSend channel: '#PipeLine', color: 'green', message: 'asdasd', tokenCredentialId: 'slack'
      }
    
    }
    
    
    
    
    
  }


}
