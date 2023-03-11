pipeline{
    agent any
    tools{
        maven 'local_maven'
    }
    stages{
        stage ('Build'){
            steps{
                sh 'mvn clean package'
           }
           post{
               success{
                    echo "Archiving the Artifacts"
                    acrhiveArtifacts arttifacts: '**/target/*.war'
               }
            }
        }
        stage ('Deploy to tomcat server') {
            steps{
                deploy adapters: [tomcat8(path: '', url: 'http://34.201.15.106:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}