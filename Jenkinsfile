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
            steps {
                withSonarQubeEnv('sonar-scanner') {
                    script {
                        def scannerHome = tool 'sonar-scanner'
                        bat "${scannerHome}C/Sonarqube/sonar-scanner-4.1.0.1829-windows/bin"
                    }
                }
            }
        }
    }
}
