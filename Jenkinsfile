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
        sh "aws s3 cp  rectangle-*.jar http://s3.amazonaws.com/seis66502-dan/
    }
}
