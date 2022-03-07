pipeline {
    agent any

    environment {
        ITVERSITY = credentials('itversity')
    }

    tools {
        maven 'maven384'
    } 
    stages {
        stage('Compile') { 
            steps {
                sh 'cd SparkWordCount && mvn clean compile'
            }
        }
        stage('Unit Test') { 
            steps {
                sh 'cd SparkWordCount mvn clean test'
            }
        }
        stage('Package') { 
            steps {
                sh 'cd SparkWordCount mvn clean package'
            }
        }
        stage('Deploy') {
            parellel {
                stage('gw02') {
                    steps {
                    sh 'sshpass -p $ITVERSITY_PSW ssh $ITVERSITY_USR@gw02.itversity.com hostname'
                    }
                }
                stage('gw03') {
                    steps {
                    sh 'sshpass -p $ITVERSITY_PSW ssh $ITVERSITY_USR@gw03.itversity.com hostname'
                    }
                }
            }
        }
    }
}
