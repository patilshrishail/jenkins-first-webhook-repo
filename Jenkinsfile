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
        stage ('Test Application') {
            steps {
                echo 'Testing the Application'
            }
        }
        stage ('Nexus Deploy') {
             steps {
                echo 'Deploying Artifact to Nexus'
            }
        }
        stage ('Deploy to stagging Enviornment') {
            steps {
                build job : 'Deploy-web-Application-pipeline'
            }
        }


    
    }

    
}