
pipeline {
    agent any
    stages {
        stage('Browser Tests') {
            parallel {
                stage('Chrome') {
                    steps {
                        echo "Chrome Tests"
                    }
                }
                stage('Firefox') {
                    steps {
                        echo "Firefox Tests"
                    }
                }
            }
        }
    }
}