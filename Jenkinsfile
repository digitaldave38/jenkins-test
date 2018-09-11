pipeline {
    agent {
        node { label 'master' }
    }
    triggers {

    }
    environment {


    }
    parameters {

    }
    stages {
        stage("Build") {
            agent {
                docker {
                reuseNode true
                image 'hello-world:latest'
                }
            }
         }
    }
}