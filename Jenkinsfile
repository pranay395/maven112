pipeline
{
    agent any
    stages
    {
        stage('continuousDownloads')
        {
            steps
            {
                git 'https://github.com/pranay395/maven112.git'
            }
        }
        stage('continuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('continuousDeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '8be0084a-4288-40dc-9634-fc085c98e8fc', path: '', url: 'http://172.31.21.191:8080')], contextPath: 'test1', war: '**/*.war'
            }
        }
        stage('continuousTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git' 
                sh 'java -jar /home/ubuntu/.jenkins/workspace/DeclarativePipeline/testing.jar'
            }
        }
        stage('continuousDelivery')
        {
            steps
            {
                input message: 'Waiting for Approval from the DM!', submitter: 'srinivas'
                deploy adapters: [tomcat9(credentialsId: '8be0084a-4288-40dc-9634-fc085c98e8fc', path: '', url: 'http://172.31.24.74:8080')], contextPath: 'prod1', war: '**/*.war'
            }
        }
    }
}
