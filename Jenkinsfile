pipeline {
    agent any
    tools {
        maven "maven-demo"
    }
    stages {
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "archiving the artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        } 
          stage('deploy to tomcat server'){
            steps{
            deploy adapters: [tomcat8(credentialsId: 'tomcat_deployer', path: '', url: 'http://54.185.230.86:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}

