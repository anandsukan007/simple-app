pipeline {
    agent any
    tools {
        maven 'maven'
    }
    
    stages{
        stage('Build'){
            steps{
                 sh 'mvn clean package'
                 //archiveArtifacts artifacts: 'target/*.war', onlyIfSuccessful: true
            }
        }
        
        stage('Upload War To Nexus'){
            steps{
                /*script{

                    def mavenPom = readMavenPom file: 'pom.xml'
                    def nexusRepoName = mavenPom.version.endsWith("SNAPSHOT") ? "simpleapp-snapshot" : "simpleapp-release" */
                    nexusArtifactUploader artifacts: [
                        [
                            artifactId: 'simple-app', 
                            classifier: '', 
                           // file: "target/simple-app-1.0.0.war", 
                            file: "target/simple-app-1.0.0.war",
                            type: 'war'
                        ]
                    ], 
                    credentialsId: 'nexus', 
                    groupId: 'in.javahome', 
                    nexusUrl: '172.31.10.168:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'http://3.108.236.189:8081/#admin/repository/repositories:simpleapp-release/', 
                    version: "1.0.0"
                    }
            }
        }
    }

