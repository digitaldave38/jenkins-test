pipeline {
    agent {
        node { label 'master' }
    }
  
    environment {
        MY_TEST = ""


    }
    parameters {
        string(name: 'test', defaultVaule: '', description: 'test')


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