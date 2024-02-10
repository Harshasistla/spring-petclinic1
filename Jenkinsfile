pipeline {
    agent any
    options { 
        timeout(time: 30, unit: 'MINUTES') 
    }
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('git') {
            steps {
                git url: 'https://github.com/konduriakhil/spring-petclinic.git', 
                    branch: 'sonar'
            }

        }
        stage('build'){
            steps{
                sh 'mvn clean package'
                }
            }
        }
 }        