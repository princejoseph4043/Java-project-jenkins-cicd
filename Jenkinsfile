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
        sh 'mvn clean install -f MyWebApp/pom.xml'
      }

    }
  }
}
