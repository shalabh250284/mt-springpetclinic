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
                AWS_DEFAULT_REGION= "us-east-1"
            }            
            steps {
                echo 'cloudformation deploy'
                sh 'aws cloudformation deploy --template-file ./cfn-alb-asg.yml --stack-name my-spring-stack --parameter-overrides VPC=vpc-930695ee PubSubnetZoneA=subnet-9ec588bf PubSubnetZoneB=subnet-d66de7e7 PubSubnetZoneC=subnet-913e78f7 PubSubnetZoneD=subnet-274c0f78 PubSubnetZoneE=subnet-b93e06b7 PubSubnetZoneF=subnet-833523ce KeyName=key-045ebb19f6e7ff88d'
            }
        }        
    }
}