node('built-in') 
{
    stage('ContinuousDownload') 
    {
         git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('ContinuousBuild') 
    {
         sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        deploy adapters: [tomcat9(credentialsId: 'f1af9dcf-4b4b-450b-97d8-fe2203953784', path: '', url: 'http://172.31.20.40:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline2/testing.jar'
        
    }
    stage('ContinuousDelivery')
    {
        deploy adapters: [tomcat9(credentialsId: 'f1af9dcf-4b4b-450b-97d8-fe2203953784', path: '', url: 'http://172.31.25.20:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
    
    
    
    
    
}
