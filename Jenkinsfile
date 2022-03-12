pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: '9f567119-2180-4a73-b91c-d8f2654a7a36', path: '', url: 'http://172.31.43.192:8080')], contextPath: 'test', war: '**/*.war'
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
               git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
          
            }
        }
       
    }
    
    post
    {
        success
        {
               deploy adapters: [tomcat9(credentialsId: '9b87e639-2fa1-4606-b6bb-2733ffc25871', path: '', url: 'http://172.31.3.205:8080')], contextPath: 'prod', war: '**/*.war'
        }
       
    }
    
    
    
    
    
    
}
