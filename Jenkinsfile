pipeline {
    agent any
    
    triggers{
        pollSCM('* * * * *')
    }
    stages{
        stage('Build'){
            steps{
            sh 'mvn clean package'
	    sh "sudo docker build -t tomcat:${env.BUILD_ID} . "
        }
        }
    }
}
