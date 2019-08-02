node {
   
   stage('Code Checkout') { 
  git credentialsId: 'github', url: 'https://github.com/anaganipratheep/maven-examples.git'     
    }
   stage('Build') {
    withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
      sh 'mvn clean compile'
      }
    }
   stage('Unit Test run') {
    withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
     sh 'mvn test'
      } 
    }
   
   withSonarQubeEnv(credentialsId: 'sonarid') {
    withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
    sh 'mvn sonar:sonar-sonar.projectKey=pratheep1993_maven-examples -Dsonar.organization=pratheep1993 -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=a4ff6418a1ae790dce1e35e3517bca92342ac741' 
      }
    }
   
    }
 
   stage('Package to Jfrog') {
    withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
     sh 'mvn package'
      }
    }
   
   stage('Deploy to Dev') {
     
    }
   stage('Automation Testing') {
     
    }
   stage('Deploy to Test') {
     
    }
   stage('Smoke Testing') {
     
    }
   stage('Deploy to Prod') {
     
    }
   stage('Acceptance Testing') {
     
    }
