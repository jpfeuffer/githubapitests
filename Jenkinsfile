pipeline {
  agent master
  stages {
    stage('echo') {
      steps {
        parallel(
          "echo_win": {
            node(label: 'win8') {
              script { def winnode = env.NODE_NAME }
              sh '''#!bash
echo "win" > win.txt'''
            }
          },
          "echo_lnx": {
            node(label: 'ubuntu_1404') {
              script { def lnxnode = env.NODE_NAME }
              sh '''#!bash
echo "ubuntu" > ubuntu.txt'''
            }
          },
          "echo_style": {
            node(label: 'ubuntu_1404') {
              script { def lnxnode2 = env.NODE_NAME }
              sh '''#!bash
echo "style" > style.txt'''
            }
          }
        )
      }
    }
    stage('deploy') {
      steps {
        parallel(
          "deploy_win": {
            node(label: winnode) {
              sh '''#!bash
              cat win.txt'''
            }
          },
          "deploy_lnx": {
            node(label: lnxnode) {
              sh '''#!bash
              cat ubuntu.txt'''
            }
          }
        )
      }
    }
  }
}
