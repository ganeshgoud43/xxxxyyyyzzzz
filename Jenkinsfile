pipeline
{
    agent any
    stages
    {
        stage('Download')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/maven.git'
            }
            
        }
        stage('Build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('Deployment')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/Declarativepipeline/webapp/target/webapp.war ubuntu@172.31.6.204:/var/lib/tomcat10/webapps/testapp1.war'
            }
        }
        stage('Testing')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/Declarativepipeline/testing.jar'
            }
        }
        stage('Delivery')
        {
            steps
            {
                 sh 'scp /var/lib/jenkins/workspace/Declarativepipeline/webapp/target/webapp.war ubuntu@172.31.13.234:/var/lib/tomcat10/webapps/prodapp1.war'
            }
         }
    }
}
