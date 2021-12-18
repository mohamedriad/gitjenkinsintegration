properties([pipelineTriggers([githubPush()])]) // trigger pipeline to commits
properties([parameters([choice(choices: "master\nfeature-1\nfeature-2", name: 'branch')])]) // parameters in pipeline
//node { git url: 'https://github.com/mohamedriad/gitjenkinsintegration.git', branch:'master' } // checkout believe we dont need it
pipeline{
  agent any
  enviroment{
    PATH= '/opt/maven3/bin:$PATH'  //zy enk bt-add msln java fel path fel windows 
  }
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
        slackSend channel: '#PipeLine',
            color: 'green',
            message: 'asdasd',
            tokenCredentialId: 'slack'
      }
    
    }
    
    
    
    
    
  }


}
