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
 
       
    }
    
}
