
pipeline {
    agent any
    stages {
        stage('BUILD'){
            steps{
                echo 'mvn clean package'
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