@Library('java_demo_pipeline@main') _
pipeline {
    agent {
        label 'slave2'
    }
    stages {
        stage('Checkout') {
            steps {
               checkoutcode('hello_world')
            }
        }
        
        stage('build') {
            steps {
               //sh "cd webdemohost"
              // sh "mvn clean package"
                buildproject('hello_World')
            }
        }
        stage('publish') {
            steps {
               //sh "cd webdemohost"
               sh "mvn clean deploy"
               // buildproject('hello_World')
            }
        }

           stage('download') {
            steps {             
            
withCredentials([string(credentialsId: 'jfrog_token', variable: 'JFROG_API_TOKEN')]) {
                        sh '''
                        curl -L -u  "basavarajmallad@gmail.com:\${JFROG_API_TOKEN}" -o "basavaraj-mallad-1.0.0.war" "https://trialkn4ife.jfrog.io/artifactory/hello-world-war-libs-release/com/efsavage/hello-world-war/3.1.1/hello-world-war-3.1.1.war"
                        '''
}
            }
        }
        
        
        stage('deploy') {
            steps {             
                //sh "cp target/*.war /opt/apache-tomcat-10.1.35/webapps/"
                sh "cp basavaraj-mallad-1.0.0.war  /opt/apache-tomcat-10.1.35/webapps/"
            }
        }
    }
}
