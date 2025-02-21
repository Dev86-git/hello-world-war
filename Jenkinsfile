@Library('library_dependnacy@main') _
pipeline {
    agent { label 'slave4' }

    parameters {
        string(name: 'command1', description: 'Give build the command')
        choice(choices: ['package', 'compile', 'install'], name: 'command2')
    }

    stages {
        stage('Checkout') {             
            steps {
               // sh "rm -rf hello-world-war"
               // sh "git clone https://github.com/Dev86-git/hello-world-war.git"
                checkoutcode()
            }
        }

        stage('Build') {
            steps {
               // sh "cd hello-world-war"
                // sh "mvn clean package"
                buildproject()
                        }
        }
        stage('download') {
            steps {             
            
withCredentials([string(credentialsId: 'jfrogtoken', variable: 'JFROG_API_TOKEN')]) {
                        sh '''
                        curl -L -u  "devarajkushi@gmail.com:\${JFROG_API_TOKEN}" -o "devraj-kushi-1.0.0.war" "https://trialfb6xdx.jfrog.io/artifactory/hello-world-war-libs-release/com/efsavage/hello-world-war/3.1.1/hello-world-war-3.1.1.war"
                        '''
}
            }
        }

        stage('Deploy') {
            steps {
                sh "cp target/*.war /opt/apache-tomcat-10.1.35/webapps/"
            }
        }
    }
}
