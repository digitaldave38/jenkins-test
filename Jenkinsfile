pipeline {
    agent {
        node { label 'master' }
    }
  
    environment {
        MY_TEST = "hjghjgjhghjghjghjg"
    }

    parameters {
        string(name: 'test', defaultValue: '', description: 'test')
        string(name: 'docker-image', defaultValue: 'python:3.5.1', description: 'docker image')
        )
   }


    stages {
        stage("Build") {
            agent {
                docker {
                reuseNode true
                image ${params.docker-image}
                }
            }
            steps {
                echo "running ${params.docker-image}"
                sh 'python --version'
            }
        }
        stage("Destroy build") {
           steps {
               echo "delete ${params.docker-image}"
               sh 'docker rmi $(docker images -a -q) --force'
           } 
        }
    }
}   