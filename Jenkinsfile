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
            pathSonarProperties = 'sonar-project.properties'
          }
            steps {
                withSonarQubeEnv('sonardocker') {

                     bat 'mvn sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.login=0b3820907f5ad45b045e6073a51c933e38713cb3'


                }
            }
        }
    }
}
