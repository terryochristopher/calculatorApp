pipeline{
    agent any
    tools{
        maven 'maventomcat'
    }
     stages {
            stage('build') {
                steps {
                    echo 'Building..'
            sh '/opt/homebrew/Cellar/maven/3.9.0/libexec package'
                }
            }
            stage('test') {
                steps {
                    echo 'Building..'
            sh '/opt/homebrew/Cellar/maven/3.9.0/libexec test'
                }
            }
            stage('deploy') {
                steps {
                    echo 'Deploying....'
            deploy adapters: [tomcat8(credentialsId: 'admin', path: '', url: 'http://localhost:9090/')], contextPath: null, war: '**/*.war'
                }
            }
        }
    }
