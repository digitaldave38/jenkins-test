pipeline {
    agent {
        node { label 'master' }
    }
  
    environment {
        MY_TEST = "hjghjgjhghjghjghjg"
    }

    parameters {
        string(name: 'test', defaultValue: '', description: 'test')
        string(name: 'docker-test', defaultValue: 'python:3.5.1', description: 'docker image')
   }


    stages {
        stage("Build") {
            agent {
                docker {
                reuseNode true
                image "'${params.docker-test}''"
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