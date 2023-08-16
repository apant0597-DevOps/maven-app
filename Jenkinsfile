
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
	    post {
		    always {
			    junit 'target/surefire-reports/*.xml'
		    }
	    }
        }
	stage('DEPLOY'){
            steps {
                sshagent(['jenkins-agent-creds']) {
                    sh '''
                
                    scp -o StrictHostKeyChecking=no target/tomcat-app.jar ec2-user@172.31.27.181:/opt/tomcat9/webapps
                    ssh ec2-user@172.31.27.181 /opt/tomcat9/bin/shutdown.sh
                    ssh ec2-user@172.31.27.181 /opt/tomcat9/bin/startup.sh
                
                    '''
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
