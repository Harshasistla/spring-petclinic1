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
                sh 'mvn clean package'
                withSonarQubeEnv(installationName: 'SONAR_CLOUD', credentialsId: 'SONAR_CLOUD') {
                   sh  'mvn clean verify sonar:sonar -Dsonar.host.url=https://sonarcloud.io -Dsonar.organization=testakhil -Dsonar.projectKey=testakhil_test'
                }
            }
        }
    }
}        