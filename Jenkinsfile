pipeline {
    agent{
        node{
            lable 'master'
            customWorkspace 'SMARTShip'
        }
    }
    triggers{
        pollSCM('* * * * *')
    }
    stages{
        stage('Build'){
            steps{
            sh 'mvn clean package'
        }
        }
    }
}
