pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                sh 'mvn -f java-tomcat-sample/pom.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Create the Docker image out of generted War file'){
            steps{
                sh 'docker build . -t tomcat_sample_java:${env.BUILD_NUMBER}"'

            }
            
        }
       
    }
}
