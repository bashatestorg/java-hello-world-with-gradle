pipeline {
    agent any
    environment {
        JAVA_HOME = 'C:\\Program Files\\Java\\jdk-17' // Update this with the path to Java 17 installation directory
    }
    stages {
        stage('Clean Workspace') {
            steps {
                deleteDir()
            }
        }
        stage('Clone Project') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                bat './gradlew.bat clean build'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                script {
                    bat './gradlew.bat sonarqube \
                        -Dsonar.projectKey=sample_gradle_java \
                        -Dsonar.projectName=\'sample_gradle_java\' \
                        -Dsonar.host.url=http://localhost:9000 \
                        -Dsonar.login=sqp_7efe6068a2ba16be8bd78bc1214703290fb639fd'
                }
            }
        }
    }
}
