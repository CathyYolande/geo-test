pipeline{
    agent any 
    stages{
        stage('maven clean'){
        steps{
            sh 'mvn clean'
        }
        }
        stage('maven install'){
            steps{
                sh 'mvn install'
            }
        }
        stage('maven package'){
            steps{
                sh 'mvn package'
            }
        }
        stage ('upload artifact'){
            steps{
                nexusArtifactUploader artifacts: [[artifactId: 'bioMedical', classifier: '', 
                file: 'target/bioMedical-0.0.2-SNAPSHOT.jar', type: 'jar']], credentialsId: 'nexusID', groupId: 'qa',
                 nexusUrl: 'ec2-3-87-71-81:8081', nexusVersion: 'nexus3',
                  protocol: 'http', repository: 'noella-repo', version: '0.0.2-SNAPSHOT'
            }
        }
    }
}