pipeline
{
    agent any
    stages
    {
        stage('Continuous Download')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'

            }
        }
        stage('Continuos build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('Continuous deploy')
        {
            steps
            {
                sh 'scp /home/ubuntu/.jenkins/workspace/development/webapp/target/webapp.war ubuntu@172.31.23.14:/var/lib/tomcat9/webapps/Qae1.war'
            }
        }
        stage('Continous testing')
        {
            steps
            {
                git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
                sh 'java -jar /home/ubuntu/.jenkins/workspace/development/testing.jar'
                
            }
        }
        stage('Continuous delivery')
        {
            steps
            {
                sh 'scp /home/ubuntu/.jenkins/workspace/development/webapp/target/webapp.war ubuntu@172.31.25.159:/var/lib/tomcat9/webapps/prod1.war'

            }
        }
    }
}
