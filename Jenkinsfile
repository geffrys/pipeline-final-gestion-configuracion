
pipeline{
    agent any;

    parameters {
        string(name: 'GITHUB_URL', defaultValue: 'https://github.com/geffrys/proyecto-web-final-gestion-configuracion', description: 'URL del repositorio de GitHub')
        string(name: 'EMAIL', defaultValue: 'geffry.ospina@gmail.com', description: 'Correo electrónico del usuario de GitHub')
    }

    tools {
        maven 'maven 3.9.6'
    }

    stages {
        stage('Listar archivos del workspace actual') {
            steps {
                bat 'dir'
            }
        }
        stage('Limpiar workspace') {
            steps {
                bat '''
                    echo Limpiando el workspace...
                    mkdir temp_dir
                    move * temp_dir
                    rmdir /s /q temp_dir
                '''
            }
        }
        stage('Clonar repository') {
            steps {
                bat "git clone ${params.GITHUB_URL}"
            }
        }
        stage('Maven build') {
            steps {
                bat ''''
                    cd proyecto-web-final-gestion-configuracion
                    mvn clean package
                '''
            }
        }
    }
}
