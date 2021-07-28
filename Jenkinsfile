pipeline {
    agent any
    tools {
        maven 'Maven3.8.1'
    }
    stages{
        stage("Build"){
            steps{
                sh 'mvn clean package'
            }
        }
        stage("Upload war to Nexus"){
            steps{
                nexusArtifactUploader artifacts: [
                    [
                        artifactId: 'simple-app', 
                        classifier: '', 
                        file: 'target/simple-app-3.0.0.war', 
                        type: 'war'
                    ]
                ], 
                credentialsId: 'NEXUS_CRED', 
                groupId: 'in.javahome', 
                nexusUrl: '10.128.0.33:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'http://34.133.161.229:8081/repository/simpleapp-release/', 
                version: '3.0.0'
            }
        }
    }
}
