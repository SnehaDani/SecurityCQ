pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                    sh label: '', script: ' mvn clean package crx:install -Dinstance.url=http://54.171.245.132:5000 -Dinstance.username=admin -Dinstance.password=admin'
            }
        }
        stage('second test') { 
            steps {
               sh label: '', script: ' mvn clean package -Pcli'
            }
        }
        stage('Deploy') { 
            steps {
                 
            sh label: '', script: ' java -jar target/secure-aem-1.3.3-SNAPSHOT.jar -a http://54.171.245.132:5000 -aCredentials admin:admin'
            sh "ssh -o StrictHostKeyChecking=no 'echo $HOME'"

             
            }
        }
    }
}
