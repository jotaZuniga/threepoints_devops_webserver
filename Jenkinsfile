pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'jotaZuniga', url: 'https://github.com/jotaZuniga/threepoints_devops_webserver'
            }
        }
        stage('Pruebas de SAST') {
            parallel {
              stage('SAST simple echo') {
                steps {
                    echo 'Ejecución de pruebas de SAST'
                }
              }
              
              stage('Imprimir Env') {
                  steps {
                      echo "My path is: ${env.WORKSPACE}"
                  }
              }
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
