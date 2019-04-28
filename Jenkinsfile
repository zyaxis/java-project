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
    
    stage('Deploy'){
        aws s3 mb s3://seis66502-dan-assignment10
    }
}
