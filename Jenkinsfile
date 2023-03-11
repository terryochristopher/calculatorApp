pipeline{
    agent any
    tools{
        maven 'local_maven'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
           }
           stage('test') {
             steps {
                    echo 'Testing..'
                    'mvn test' '**/target/*.war'
               }
            }
        }
        stage('Deploy to tomcat server') {
            steps {
                deploy adapters: [tomcat8(credentialsId: 'd0408b5d-ddf2-407a-b9fb-c3b1504bacd3', path: '', url: 'http://34.201.15.106:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
