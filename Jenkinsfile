node {
  stage('SCM') {
    checkout scm
  }
 stage('SonarQube Analysis') {
            when {
                  expression { BRANCH_NAME ==~ /($GIT_BRANCH)/ }
        	}
             steps {
                 withSonarQubeEnv(credentialsId: 'sonar', installationName: 'sonarqube') {
       				sh './mvnw clean verify sonar:sonar -Dmaven.test.skip=true -Dsonar.projectKey=sonar-git'
     			}
             }
         }
}
