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
   
   stage('sonarQube stage') {
    withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
    sh 'mvn clean compile sonar:sonar -Dsonar.projectKey=maven-exampl -Dsonar.organization=anaganipratheep -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=7ba042578d773d71c8694e40fe36964e577a9c3f' 
      }
    }
  stage("Quality Gate"){
          timeout(time: 1, unit: 'HOURS') {
              def qg = waitForQualityGate()
              if (qg.status != 'OK') {
                  error "Pipeline aborted due to quality gate failure: ${qg.status}"
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
}
