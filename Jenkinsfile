
    node('java') {
    stages {
	    
        stage('checkout') {
 
            steps {
   sh 'git clone https://github.com/mjgoutham/hello-world-war.git'
            }
        }
		        stage('build') {
				
            steps {
  sh 'mvn clean package'
            }
        }
          
	
    }
}
