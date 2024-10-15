pipeline {     
    agent { label 'slave-1' } 
    
    tools {
        jdk 'jdk17'  // Ensure this matches the configured JDK name in Jenkins
        maven 'maven3'
    } 

    stages {
        stage('Check Environment') {
            steps {
                script {
                    // Manually set JAVA_HOME to the correct JDK path
                    env.JAVA_HOME = "/home/ubuntu/jenkins-workspace/tools/hudson.model.JDK/jdk17"
                    echo "JAVA_HOME: ${env.JAVA_HOME}"
                    sh 'java -version'
                    sh 'which java'
                }
            }
        }

        stage('Compile') {
            steps {
                script {
                    // Ensure JAVA_HOME is properly exported before running Maven
                    sh 'export JAVA_HOME=/home/ubuntu/jenkins-workspace/tools/hudson.model.JDK/jdk17 && mvn compile'
                }
            }
        }
        
        stage('Tests') {
            steps {
                sh "export JAVA_HOME=/home/ubuntu/jenkins-workspace/tools/hudson.model.JDK/jdk17 && mvn test"
            }
        }
        
        stage('Build') {
            steps {
                sh "export JAVA_HOME=/home/ubuntu/jenkins-workspace/tools/hudson.model.JDK/jdk17 && mvn package"
            }
        }
    }
}
