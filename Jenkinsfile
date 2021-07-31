pipeline {
    agent any 
    tools { 
        maven 'Maven 3.5.2' 
        jdk 'jdk1.8.0.151' 
    }
    stages {
        stage('Example Build') {
            steps {
                echo 'Hello, Maven'
                sh 'mvn --version'
            }
        }
        // stage('Example Test') {
        //     steps {
        //         echo 'Hello, JDK'
        //         sh 'java -version'
        //     }
        // }
    }
}