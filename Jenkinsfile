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
                def mavenPom = readMavenPom 'pom.xml'
                nexusArtifactUploader artifacts: [
                    [
                        artifactId: 'simple-app', 
                        classifier: '', 
                        file: "target/simple-app-${mavenPom.version}.war", 
                        type: 'war'
                    ]
                ], 
                credentialsId: 'NEXUS_CRED', 
                groupId: 'in.javahome', 
                nexusUrl: '10.128.0.33:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'simpleapp-release/', 
                version: "${mavenPom.version}"
            }
        }
    }
}
