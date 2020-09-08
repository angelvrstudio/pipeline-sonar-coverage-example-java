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
                bat 'mvn clean install -U'
            }
        }

        stage('QA-Sonar') {


            steps {
                withSonarQubeEnv('sonardocker') {

                    script {

                     def scannerHome = tool 'sonar-scanner'
                     bat "${scannerHome}/bin/sonar-scanner"

                     }
                }
            }
        }
    }
}
