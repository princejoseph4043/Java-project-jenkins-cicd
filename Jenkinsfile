node{
   stage('Clone repository') {
        git branch: "master", url: "https://github.com/princejoseph4043/Java-project-jenkins-cicd.git"
    }
   stage('Mvn Package'){
     def mvnHome = tool name: 'maven-3', type: 'maven'
     def mvnCMD = "${mvnHome}/bin/mvn"
     sh "${mvnCMD} clean package"
   }
   stage('Build Docker Image'){
     sh 'docker build -t kammana/my-app:2.0.0 .'
   }
}
