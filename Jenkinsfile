pipeline {
    agent any 
    tools { 
        maven 'Maven-3.5.2' 
        jdk 'jdk1.8' 
    }
    stages {
        stage('Example Build') {
            steps {
                echo 'Hello, Maven'
                sh 'mvn install'
                // sh 'mvn --version'
            }
        }
        // stage('AWS Test') {
        //     steps {
        //         echo 'Hello, JDK'
        //         sh 'java -version'
        //     }
        // }
        stage('AWS Test') {
            environment {
                AWS_ACCESS_ID = credentials('jenkins-aws-secret-key-id')
                AWS_ACCESS_KEY_ID = "${env.AWS_ACCESS_ID_USR}"
                AWS_SECRET_ACCESS_KEY = "${env.AWS_ACCESS_ID_PSW}"
            }            
            steps {
                echo 'Testing AWS Connections'
                sh 'aws s3 ls'
            }
        }        
    }
}