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
        sh "aws cloudformation describestack-resources --region us-east-1 --stack-name jenkins"
    }
}
