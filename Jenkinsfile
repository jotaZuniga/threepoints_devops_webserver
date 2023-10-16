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
        
        stage('Configurar archivo') {
            environment {
                PRACTICA_CREDENTIALS = credentials('Credentials_Threepoints')
            }
            steps {
                script {
                    def data = "[credentials]\nuser=$PRACTICA_CREDENTIALS_USR\npassword=$PRACTICA_CREDENTIALS_PSW\n"
                    writeFile(file: 'credentials.ini', text: data)
                    sh "ls -l"
                }
            }
        }
        
        stage('Read') {
            steps {
                script {
                    def data = readFile(file: 'credentials.ini')
                    println(data)
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
