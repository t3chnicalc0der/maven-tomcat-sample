pipeline {     
    agent { label 'slave-1' } 
    
    tools {
        jdk 'jdk17'
        maven 'maven3'
    } 

    stages {
        stage('Preparation') {
            steps {
                echo "Preparing to build on agent: ${env.NODE_NAME}"
                echo "JAVA_HOME: ${env.JAVA_HOME}"
                echo "MAVEN_HOME: ${env.MAVEN_HOME}"
            }
        }

        stage('Compile') {
            steps {
                echo 'Compiling the project...'
                sh 'mvn compile'
            }
        }
        
        stage('Tests') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building the project...'
                sh 'mvn package'
            }
        }
    }
}
