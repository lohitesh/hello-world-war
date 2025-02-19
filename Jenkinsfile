pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {	
		
                sh 'git clone https://github.com/lohitesh/hello-world-war/'
            }
        }
	stage('Build') {
	when {
                branch 'develop'
	}
            steps {		
                sh 'mvn clean package'
            }
        }

	stage('Push artifacts into artifactory') {
	when {
                not {
                    branch 'main'
                }
            }
            steps {
              rtUpload (
                serverId: 'my-artifactory',
                spec: '''{
                      "files": [
                        {
                          "pattern": "*.war",
                          "target": "example-repo-local/"
                        }
                    ]
                }'''
              )
	    }
	}
	    
	stage('Deploy') {
            steps {		
			
                sh 'echo Deployed'

            }
        }
	    
    }
}
