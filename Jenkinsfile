  agent none
    stages {
        stage('Back-end') {
        stage('Build') {
            agent {
                docker {
                    image 'python:2-alpine'
                }
            }
            steps {
                sh 'python -m py_compile sources/add2vals.py sources/calc.py'
            }
        }
        stage('Test') {
            agent {
                docker { image 'maven:3-alpine' }
                docker {
                    image 'qnib/pytest'
                }
            }
            steps {
                sh 'mvn --version'
                sh 'py.test --verbose --junit-xml test-reports/results.xml sources/test_calc.py'
            }
            post {
                always {
                    junit 'test-reports/results.xml'
                }
            }
        }
        stage('Front-end') {
        stage('Deliver') { 
            agent {
                docker { image 'node:7-alpine' }
                docker {
                    image 'cdrx/pyinstaller-linux:python2' 
                }
            }
            steps {
                echo $"{MY_TEST}"
                sh 'node --version'
    
           } 
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
} 