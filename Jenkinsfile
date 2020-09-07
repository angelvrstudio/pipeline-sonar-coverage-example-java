pipeline {
    agent any
    tools {
        maven 'apache-maven-3.5.0'
    }


    stages {
        stage('Compile Stage') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('QA-Sonar') {

          environment {
            SCANNER_HOME = tool 'sonar-scanner'
          }
            steps {
                withSonarQubeEnv('sonardocker') {

                     bat '''$SCANNER_HOMEC/Sonarqube/sonar-scanner-4.1.0.1829-windows/bin
                                 -Dsonar.java.binaries=target/classes
                                 -Dsonar.projectKey=sonar-coverage-example-java
                                 -Dsonar.sources=src/main/java'''

                }
            }
        }
    }
}
