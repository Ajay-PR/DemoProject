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
    }
}
