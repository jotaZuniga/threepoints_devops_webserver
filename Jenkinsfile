pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'jotaZuniga', url: 'https://github.com/jotaZuniga/threepoints_devops_webserver'
            }
        }
        stage('Pruebas de SAST') {
            steps {
                echo 'Ejecución de pruebas de SAST'
            }
        }
        stage('Build') {
            steps {
                script {
                    docker.build("devops_ws")
                }
            }
        }
    }
}
