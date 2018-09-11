pipeline {
    agent {
        node { label 'master' }
    }
  
    environment {
        MY_TEST = "hjghjgjhghjghjghjg"
    }

    parameters {
        string(name: 'test', defaultValue: '', description: 'test')
        string(name: 'docker-test', defaultValue: '', description: 'docker image')
   }


    stages {
        stage("Build") {
            agent {
                docker {
                image 'python:3.5.1' 
                args '-u root:root'
                }
            }
            steps {
                echo "running ${params.docker-test}"
                sh 'python --version'
            }
        }
        stage("Destroy build") {
           steps {
               echo "delete ${params.docker-test}"
               sh 'docker rmi $(docker images -a -q) --force'
           } 
        }
    }
}   