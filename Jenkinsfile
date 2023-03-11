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
           stage('test'){
             steps{
                    echo 'Testing..'
                    'mvn test' '**/target/*.war'
               }
            }
        }
        stage ('Deploy to tomcat server') {
            steps{
                deploy adapters: "scp -o StrictHostKeyChecking=no,deploy adapters: [tomcat8(path: '', url: 'http://34.201.15.106:8080/')], contextPath: null, war: '**/*.war"
            }
        }
    }
}