node{
    
echo  "The job name is: ${env.JOB_NAME}"
echo "The build number is:  ${env.BUILD_NUMBER}"
echo "The Node name is:  ${env.JOB_NAME}"
echo "The Jenkins HD is:  ${env.JENKINS_HOME}"
echo "The Jenkins url is:  ${env.JENKINS_URL}"
echo "The job url is:  ${env.JOB_URL}"


   properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '3')), pipelineTriggers([pollSCM('* * * * *')])])
    
def mavenHome = tool name: 'maven3.8.6'

stage('CheckOutCodeGit'){
git branch: 'development', credentialsId: '3b8002a2-f2a8-4726-814b-98ef45205015', url: 'https://github.com/petergillgithub/maven-web-application.git'
}	

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}

/*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('UploadArtifactsIntoNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}

stage ('DeployAppintoTomcatServer'){
sshagent(['c1bce653-5b97-424d-a421-f09076e84f75']) {
    // some block
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.38.87:/opt/apache-tomcat-9.0.71/webapps/"
}
}

*/


}
