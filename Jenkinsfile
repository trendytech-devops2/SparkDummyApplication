pipeline {
    agent any
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
                sh 'cd SparkWordCount && mvn clean test' 
            }
        }
        stage('Package') { 
            steps {
                sh 'cd SparkWordCount && mvn clean package'
            }
        }
    }
}
