pipeline {
    agent {
        node { label 'master' }
    }
  
    environment {
        MY_TEST = "hjghjgjhghjghjghjg"
    }

    parameters {
        string(name: 'test', defaultValue: '', description: 'test')
   }


    stages {
        stage("Build") {
            agent {
                docker {
                reuseNode true
                image 'python:3.5.1'
                }
            }
            steps {
                sh 'python --version'
            }
        }
        stage("Destroy build") {
           }
           steps {
               sh 'docker rmi $(docker images -a -q) --force'
           } 
        }
    }