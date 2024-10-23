pipeline {
    environment {
        IMAGEN = "iancacace/myapp"
        USUARIO = 'dockerHubCred'
    }
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: "main", url: 'https://github.com/iancacace/jenkins_docker_test1.git'
            }
        }
        stage('Build') {
            steps {
                script {
                    newApp = docker.build "$IMAGEN:$BUILD_NUMBER"
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    docker.image("$IMAGEN:$BUILD_NUMBER").inside('-u root') {
                           sh 'apache2ctl -v'
                        }
                    }
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    docker.withRegistry( '', USUARIO ) {
                        newApp.push()
                    }
                }
            }
        }
        stage('Clean Up') {
            steps {
              #  sh "docker rmi $IMAGEN:$BUILD_NUMBER"
                echo "FIN"
                }
        }
    }
}
