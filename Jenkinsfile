
pipeline {
    agent any
        stages {
            stage('Build') {
                when {
                    expression {
                        "foo" == "bar"
                    }
                }
                steps {
                    echo 'Building'
                }
            }
        stage('Test') {
            when {
                environment name: 'JOB_NAME', value: 'foo'
            }
            steps {
                echo 'Testing'
            }
        }
        stage('Deploy') {
            when {
                branch 'master'
            }
            steps {
                echo 'Deploying'
            }
        }
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