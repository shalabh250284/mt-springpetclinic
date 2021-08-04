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
                //sh 'mvn install'
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
                sh 'aws cloudformation create-stack --stack-name my-spring-stack --template-body ./cfn-alb-asg.yml --parameters ParameterKey=VPC, ParameterValue=vpc-930695ee ParameterKey=PubSubnetZoneA, ParameterValue=subnet-9ec588bf ParameterKey=PubSubnetZoneB, ParameterValue=subnet-d66de7e7 ParameterKey=PubSubnetZoneC, ParameterValue=subnet-913e78f7 ParameterKey=PubSubnetZoneD, ParameterValue=subnet-274c0f78 ParameterKey=PubSubnetZoneE, ParameterValue=subnet-b93e06b7 ParameterKey=PubSubnetZoneF, ParameterValue=subnet-833523ce ParameterKey=KeyName, ParameterValue=key-045ebb19f6e7ff88d --capabilities CAPABILITY_IAM'
            }
        }        
    }
}