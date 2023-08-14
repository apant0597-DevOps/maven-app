
pipeline {
    agent any
    stages {
        stage('MAVEN BUILD'){
            steps{
                 sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('PUBLISH'){
            steps {
                echo 'SEND FOR PUBLISH'
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