node{

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

echo "Job name is: ${env.JOB_NAME}"
echo "Build Number is: ${env.BUILD_NUMBER}"
echo "Jenkins Home is: ${env.JENKINS_HOME}"
echo "Build Number is: ${env.BUILD_NUMBER}"

def mavenHome = tool name: 'Maven 3.9.8'

stage('CheckOutCode'){
git branch: 'development', credentialsId: 'aca499dc-f19b-4c72-9c2d-0d6647c923f9', url: 'https://github.com/SaranKumar516/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}             
  
/*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('UploadArtifactIntoNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}

stage('DeployIntoTomcat'){
sshagent(['60b72599-f5f7-494a-8cb3-990856466db0']) {
    // some block

sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.21.244.85:/opt/apache-tomcat-9.0.90/webapps/"
}
}
*/
  
}
