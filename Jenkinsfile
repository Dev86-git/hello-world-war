pipeline{  
agent any



    stages {
    

        stage('pull Docker Image') {
            steps {
                script {                
			sh "docker pull dev1009/test:2.0"
			
                }
            }
        }



        stage('Run Container') {
            steps {
                script {
                   sh "docker run -d  -p 8092:8080 dev1009/test:2.0"
                }
            }
        }
    }
}
