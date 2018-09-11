pipeline {
    agent {
        node { label 'master' }
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
            
            post {
        always {
            echo 'I have finished'
            deleteDir() // clean up workspace
        }
        success {
            echo 'I succeeded!'
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
        }
        changed {
            echo 'Things are different...'
            }
        }
    }
}