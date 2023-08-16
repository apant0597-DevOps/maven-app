
pipeline {
    agent any
    tools {
	    maven 'maven-jenkins'
    }
    stages {
        stage('MAVEN BUILD'){
            steps{
                 sh 'mvn -B -DskipTests clean package'
		 sh 'mv target/*.jar target/tomcat-app.jar'
            }
        }
        stage('TEST'){
            steps {
                sh 'mvn test'
            }
	    post {
		    always {
			    junit 'target/surefire-reports/*.xml'
		    }
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
