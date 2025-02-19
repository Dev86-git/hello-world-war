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
                sh "rm -rf hello-world-war"
                sh "git clone https://github.com/Dev86-git/hello-world-war.git"
            }
        }

        stage('Build') {
            steps {
                sh "cd hello-world-war"
                 sh "mvn clean package"
                        }
        }

        stage('Deploy') {
            steps {
                sh "cp target/*.war /opt/apache-tomcat-10.1.35/webapps/"
            }
        }
    }
}
