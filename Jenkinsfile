pipeline {
    agent {
        node { label 'master' }
    }
  
    environment {
        MY_TEST = "hjghjgjhghjghjghjg"
    }

    parameters {
        string(name: 'test', defaultValue: '', description: 'test')
        string(name: 'docker-test', defaultValue: 'maven:3-alpine', description: 'docker image')
   }

def username = 'maven:3-alpine'


    stages {
        stage('Back-end') {
            agent {
                docker { image ${username} }
            }
            steps {
                sh 'mvn --version'
            }
        }
        stage('Front-end') {
            agent {
                docker { image 'node:7-alpine' }
            }
            steps {
                sh 'node --version'
    
           } 
        }
    }
}   