pipeline {
    agent {
        node { label 'my-docker' }
    }
    stages {
        stage("Build") {
            agent {
                docker {
                reuseNode true
                image 'maven:3.5.0-jdk-8'
                }
            }
            steps {
                sh 'mvn install'
            }
        }
    }
}