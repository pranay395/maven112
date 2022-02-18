pipeline
{
    agent any
    stages
    {
        stage('continuousDownloads_Loanss')
        {
            steps
            {
                git 'https://github.com/pranay395/maven112.git'
            }
        }
        stage('continuousBuild_Loanss')
        {
            steps
            {
                sh 'mvn package'
            }
        } 
    }
}
