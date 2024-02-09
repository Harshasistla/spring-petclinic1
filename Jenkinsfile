pipeline {
    agent { label 'MAVEN' }
    options { 
        timeout(time: 30, unit: 'MINUTES') 
    }
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('git') {
            steps {
                git url: 'https://github.com/dummyrepos/spring-petclinic-nov23.git', 
                    branch: 'sonar'
            }

        }
        stage('build'){
            steps{
                sh 'mvn clean'
            }
        }
    }
}        