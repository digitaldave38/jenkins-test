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
                image 'hello-world:latest'
                }
            }
            steps {
                sh 'ls'
            }
        }
    }
}