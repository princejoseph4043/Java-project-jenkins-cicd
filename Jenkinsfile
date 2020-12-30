pipeline {

  tools {
  maven 'Maven3'
  }
 
  agent any
  
  stages{
  
    stage('Checkout'){
      steps {
      checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/princejoseph4043/Java-project-jenkins-cicd.git']]])
    }

    }
  
    stage('build'){
      steps{
        sh 'mvn clean install -f pom.xml'
      }
    }
    
    stage ('Code Quality') {
      steps {
        withSonarQubeEnv('sonarqube') {
        sh 'mvn -f pom.xml sonar:sonar'
        }
      }
    }
    
    stage ('Nexus upload') {
      steps {
        nexusArtifactUploader artifacts: [[artifactId: 'MyWebApp', classifier: '', file: 'target/MyWebApp.war', type: 'war']], credentialsId: 'nexus-logins', groupId: 'com.mkyong', nexusUrl: '107.23.238.72:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'simpleapp-release', version: '1.0-SNAPSHOT'
      }
    }
      
  }
}
