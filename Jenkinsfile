pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "maven-demo"
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "archiving the artifacts"
                    archiveArtofacts artifacts: '**/target/*.war'
                }
            }
          stage('deploy to tomcat server'){
            steps{
            deploy adapters: [tomcat8(credentialsId: 'tomcat_deployer', path: '', url: 'http://34.221.203.138:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
