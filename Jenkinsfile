pipeline {
    agent {
        label 'jenkins-slave'
    }
    tools {
        jdk 'jdk'
        maven 'maven'
    }
    environment {
        APPLICATION_NAME = 'eureka'
    }
    stages {
        stage('build') {
            steps{
                echo "Building ${APPLICATION_NAME}"
                sh "mvn clean package -DskipTests=true"
            }
        }
    }
}