properties([pipelineTriggers([githubPush()])]) 

node('linux')
{
    stage('Unit Tests'){
        sh "ant -buildfile text.xml"
        sh "ant -f test.xml -v"
        junit 'reports/result.xml'
    }
}
