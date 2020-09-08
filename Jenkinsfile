pipeline {
    agent any
    tools {
         jdk 'JAVA_HOME'
         maven 'MAVEN_LATEST'
    }
    environment {
            JAVA_HOME = "${jdk}"
    }


    stages {
        stage('Compile Stage') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn clean install -U'
            }
        }

        stage('QA-Sonar') {


            steps {
                withSonarQubeEnv('sonardocker') {

                    script {

                     def scannerHome = tool 'sonar-scanner'
                     sh "${scannerHome}/bin/sonar-scanner"

                     }
                }
            }
        }
    }
}
