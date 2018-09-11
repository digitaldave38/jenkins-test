pipeline {
    
    agent none 

     environment {
        ENV_STACK = 'staging'
    }
   
    parameters {
        string(name: 'RELEASE_VERSION', defaultValue: '1.0.0', description: 'Application git release tag version')
    }
   
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'python:2-alpine'
                }
            }
            steps {
                echo "Building ${params.RELEASE_VERSION} in ${env.ENV_STACK}"
                sh 'python -m py_compile sources/add2vals.py sources/calc.py'
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'qnib/pytest'
                }
            }
            steps {
                echo "Testing ${params.RELEASE_VERSION} in ${env.ENV_STACK}"
                sh 'py.test --verbose --junit-xml test-reports/results.xml sources/test_calc.py'
            }
            post {
                always {
                    junit 'test-reports/results.xml'
                }
            }
        }
        stage('Deliver') { 
            agent {
                docker {
                    image 'cdrx/pyinstaller-linux:python2' 
                }
            }
            steps {
                echo "Delivering ${params.RELEASE_VERSION} in ${env.ENV_STACK}"
                sh 'pyinstaller --onefile sources/add2vals.py' 
            }
            post {
                success {
                    archiveArtifacts 'dist/add2vals' 
                }
            }
        }
    }
}