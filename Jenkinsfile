properties([pipelineTriggers([githubPush()])]) 

node('linux')
{
    stage('Unit Tests'){
        sh "ant -buildfile test.xml"
        sh "ant -f test.xml -v"
        junit 'reports/result.xml'
    }
    
    stage('Build'){
        sh "ant"
        sh "ant -f build.xml -v"
    }
    
    stage('Report'){
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'AWS-Credentials-For-Jenkins', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
            sh "aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins"
        }
    }
}
