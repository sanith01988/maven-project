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
            sh 'mvn clean package'
        }
    }
}
