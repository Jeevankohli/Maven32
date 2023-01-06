node('built-in')
{
    stage('continuousDownload') 
    {
       git 'https://github.com/intelliqittrainings/maven.git'   
    }
    stage('continuousBuild') 
    {
         sh 'mvn package'
    }
    stage('continuousDeployment') 
    {
        deploy adapters: [tomcat9(credentialsId: 'e4d74976-171f-4a57-8554-e56099576630', path: '', url: 'http://172.31.17.136:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('continuousTesting') 
    {
         git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
         sh 'java -jar /var/lib/jenkins/workspace/scriptedpipeline1/testing.jar'
    }
     stage('continuousDelivery') 
    {
       deploy adapters: [tomcat9(credentialsId: 'a754b055-b8f0-40ee-9a5b-130e74ee23b8', path: '', url: 'http://172.31.29.86:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
    
    
}
