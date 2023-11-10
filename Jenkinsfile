node('built-in')

{
    stage('ContinousDownload') 
    {
        git 'https://github.com/chodisettivijay/mavenproj.git'
    } 
    stage('ContinousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinousDeployment')
    {
        deploy adapters: [tomcat9(credentialsId: '39ee5c89-961e-42a5-96a1-76168090ccfc', path: '', url: 'http://172.31.22.201:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinousTesting')
    {
        git credentialsId: '39ee5c89-961e-42a5-96a1-76168090ccfc', url: 'https://github.com/intelliqittrainings/FunctionalTesting.git'
    
        sh 'java -jar /var/lib/jenkins/workspace/Scriptedpipeline1/testing.jar'
    }
    stage('ContinousDelivery')
    {
        deploy adapters: [tomcat9(credentialsId: '39ee5c89-961e-42a5-96a1-76168090ccfc', path: '', url: 'http://172.31.80.179:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
    
     
}
