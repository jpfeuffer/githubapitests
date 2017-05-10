pipeline {
  agent none
  stages {
    stage('echo') {
      steps {
        parallel(
          "echo_win": {
            node(label: 'win8') {
              sh '''#!bash
echo "win" > win.txt'''
            }
            
            
          },
          "echo_lnx": {
            node(label: 'ubuntu_1404')
            
          },
          "echo_style": {
            node(label: 'ubuntu_1404')
            
          }
        )
      }
    }
    stage('') {
      steps {
        parallel(
          "deploy_win": {
            node(label: 'win8')
            
          },
          "deploy_lnx": {
            node(label: 'ubuntu_1404')
            
          }
        )
      }
    }
  }
}