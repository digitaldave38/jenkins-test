build_success = true
failed_modules = []
def proxyURL
def agentLabel
if (env.JENKINS_URL.contains('')) {
    proxyURL = "127.0.0.1:8000"
    agentLabel = "master"
} else {
    proxyURL "myproxy.mytest:8080"
    agentLabel = "testing-slave"
}
pipeline {
    agent {
        label agentLabel
    }
}
triggers {
    cron('H 17 * * 1-5')
}
environment {
    PROXY_CREDS = credentials('mytest')
    AWS_CREDS = credentials('awstest')
}
parameters {
    string(name: 'module_test_list', defaultVaule: '','Downloads the master branch')
    string(name: 'terraform_provider_aws_version', defaultVaule: '1.33.0','Downloads the master branch')
}
stages {
    stage('Ingress Teraform' {
        options {
            timeout(time: 2, unit: 'MINUTES')
            retry(3)
        }
     }
   }   
}