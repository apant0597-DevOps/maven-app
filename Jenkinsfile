
pipeline {
    agent any
    tools {
	    maven 'maven-jenkins'
    }
    stages {
        stage('MAVEN BUILD'){
            steps{
                 sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('TEST'){
            steps {
                sh 'mvn test'
            }
        }
    }
    post {
        success { 
            echo "This pipeline is successfull!"
            }
    unsuccessful {
            echo "ISSUE!!!"
            }
    }
}
