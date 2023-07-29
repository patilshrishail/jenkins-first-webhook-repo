pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                sh 'mvn -f pom.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifact"
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage ('Deploy to Staging Enviornment') {
            steps {
                script {
                    deploy adapters: [tomcat9(credentialsId: 'Tomcat-Stage-Credentials', path: '', url: 'http://3.133.140.216:8080/')], contextPath: '/', onFailure: false, war: '*/.war'
                }
            }
        }
    }
    
}