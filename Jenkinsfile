pipeline {
    agent {
        node { label 'master' }
    }
    stages {
        stage("Build") {
            agent {
                docker {
                reuseNode false
                image 'maven:3.5.0-jdk-8'
                }
            }
            steps {
                sh 'mvn install'
            }
        }
    }
}
