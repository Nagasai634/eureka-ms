pipeline {
    agent {
        label 'jenkins-slave1'
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
        stage('codequality') {
            steps {
                echo "scanning ${APPLICATION_NAME} code"
                sh """
                mvn clean verify sonar:sonar \
                      -Dsonar.projectKey=eureka-ms \
                      -Dsonar.host.url=http://34.122.117.31:9000 \
                      -Dsonar.login=sqp_748eed9b9aaa19510244007b16459219cfa845e3
                """
            }
        }
    }
}