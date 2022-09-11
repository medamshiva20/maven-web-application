node('master')
{
    stage('ContinuousDownload')
    {
        git credentialsId: '62d04095-3a03-44eb-9ae7-27a54b372c22', url: 'https://github.com/medamshiva20/maven-web-application.git'
    }
    stage('ContinuousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        sh 'scp /var/lib/jenkins/workspace/scp-pipeline/target/maven-web-application.war ubuntu@172.31.18.178:/var/lib/tomcat8/webapps/qaenv.war'
    }
    stage('ContinuousTesting')
    {
        git credentialsId: '62d04095-3a03-44eb-9ae7-27a54b372c22', url: 'https://github.com/medamshiva20/SeleniumTesting.git'
    }
    stage('ContinuousDelivery')
    {
        sh 'scp /var/lib/jenkins/workspace/scp-pipeline/target/maven-web-application.war ubuntu@172.31.11.2:/var/lib/tomcat8/webapps/prodenv.war'
    }
}
