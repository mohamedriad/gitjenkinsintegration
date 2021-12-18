properties([pipelineTriggers([githubPush()])])
node { git url: 'https://github.com/mohamedriad/gitjenkinsintegration.git', branch:'master' }
pipeline{
  agent any
  stages{
    stage('SCM'){
      steps{
        node('slave_2'){
          git 'https://github.com/mohamedriad/gitjenkinsintegration'
          sh 'python test.py'
        }

      }

    }
  }


}
