node
{
def mavenHome = tool name: "maven3.8.1"
//properties([pipelineTriggers([pollSCM('* * * * *')])])
properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
stage('checkoutcode')
{
 git branch: 'development', credentialsId: '731bced0-54b7-4949-91f7-9590171980db', url: 'https://github.com/nageshreddy456/maven-web-application.git'
 }
stage('build')
{
sh "${mavenHome}/bin/mvn clean package"
}
 /* 
stage('ExecutiveSonarQubeReport')
{
sh "${mavenHome}/bin/mvn sonar:sonar"
}
stage('UploadArtifactsintoNexus')
{
sh "${mavenHome}/bin/mvn deploy"
}
 
stage('DeploymentAppintoTomcatServer')
{
sshagent(['a4c246d1-7618-4683-afa1-33ec94f16a8e']) {
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.232.127.129:/opt/apache-tomcat-9.0.45/webapps/"
}
    
}
*/
stage('SendEmailNotification')
{
emailext body: '''Build over

Regards,
NageshwarReddy,
8639344288''', subject: 'Build over..', to: 'nageshgangireddy97@gmail.com'
}
} 
