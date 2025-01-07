pipeline {
    agent { 
        node {
            label 'docker-agent-maven'
            }
      }
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Maven-Build') {
            steps {
                echo "Maven-Building.."
                sh '''
                cd my-maven-docker-project
                mvn clean install
                '''
            }
        }
        stage('Docker-Build') {
            steps {
                echo "Docker-Building.."
                sh '''
                cd my-maven-docker-project
                docker build -t java-image:v1 .
                '''
            }
        }
        
    }
}