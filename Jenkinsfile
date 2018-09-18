pipeline
{
    agent any
    parameters{
        string(name: 'tomcat_dev', defaultValue: '192.168.1.155', description: 'Staging Server')
    }
    triggers{
        pollSCM('* * * * *')
    }
    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                     echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deployments'){
            parallel{
                stage('Deploy to Staging'){
                    steps{
                    sh "sshpass -p 'Think@123' scp **/target/*.war thinkpalm@${params.tomcat_dev}:/opt/tomcat/webapps"
                }
                }
                stage('Deploy to Production'){
                    steps{
                        sh "sshpass -p 'Think@123' scp **/target/*.war thinkpalm@${params.tomcat_dev}:/opt/tomcat-prod/webapps"
                    }
                }
            }
        }
    }
}
