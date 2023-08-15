
pipeline {
    agent any
    tools {
	    maven 'maven-jenkins'
    }
    stages {
        stage('MAVEN BUILD'){
            steps{
                 sh 'mvn -B -DskipTests clean package'
		 sh 'cp target/*.jar /home/ec2-user/Package-dir'
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
