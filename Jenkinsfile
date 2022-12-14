pipeline {
    agent none

    stages {
        stage("build and deploy on Windows and Linux") {
            parallel {
                stage("windows") {
                    agent {
                        label "win"
                    }
                    stages {
                        stage("build") {
                            steps {
                                sh '''#!bash
                                  echo "win" > win.txt
                                '''
                            }
                        }
                        stage("deploy") {
                            when {
                                branch "master"
                            }
                            steps {
                                sh '''#!bash
                                  cat win.txt
                                '''
                            }
                        }
                    }
                }

                stage("linux") {
                    agent {
                        label "ubuntu"
                    }
                    stages {
                        stage("build") {
                            steps {
                                sh 'echo "ubuntu" > ubuntu.txt'
                            }
                        }
                        stage("deploy") {
                             when {
                                 branch "master"
                             }
                             steps {
                                sh "cat ubuntu.txt"
                            }
                        }
                    }
                }
            }
        }
    }
}
