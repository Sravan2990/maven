pipeline 
{
    agent any 
    stages
    {
        stage('ContinousDownload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
       stage('ContinousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinousDeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '0c33589c-5702-49da-89bd-3b9dc4a2c6a1', path: '', url: 'http://172.31.35.105:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
        stage('ContinousTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/Declarative/testing.jar'
            }
        }
        stage('ContinousDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '0c33589c-5702-49da-89bd-3b9dc4a2c6a1', path: '', url: 'http://172.31.36.155:8080')], contextPath: 'prodapp', war: '**/*.war'
            }
        }
        
        
        
        
        
    }
    
}
