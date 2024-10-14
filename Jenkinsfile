pipeline {     
    agent { label 'slave-1' } 
    
    tools {
        jdk 'jdk17'  // This should match the name of your configured JDK in Jenkins
        maven 'maven3'
    } 

    stages {
        stage('Check Environment') {
            steps {
                script {
                    // Print JAVA_HOME set by Jenkins tool
                    echo "JAVA_HOME: ${env.JAVA_HOME}"
                    sh 'java -version'
                    sh 'which java'
                }
            }
        }

        stage('Compile') {
            steps {
                sh "mvn compile"
            }
        }
        
        stage('Tests') {
            steps {
                sh "mvn test"
            }
        }
        
        stage('Build') {
            steps {
                sh "mvn package"
            }
        }
    }
}

