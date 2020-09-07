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

                     bat 'mvn sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.login=ebe64c1ccc8d1f6c8f2f72dd59f7e12cd0b674d4'

                }
            }
        }
    }
}
