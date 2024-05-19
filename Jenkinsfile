
pipeline{
    agent any;

    parameters {
        string(name: 'GITHUB_URL', defaultValue: 'https://github.com/geffrys/proyecto-web-final-gestion-configuracion', description: 'URL del repositorio de GitHub')
        string(name: 'EMAIL', defaultValue: 'geffry.ospina@gmail.com', description: 'Correo electrónico para enviar notificaciones')
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
                    dir temp_dir
                    rmdir /s /q temp_dir
                    rmdir /s /q proyecto-web-final-gestion-configuracion
                    dir
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

    post {
        success {
            mail to: "${params.EMAIL}",
                subject: "Proyecto compilado exitosamente",
                body: "El proyecto se ha compilado exitosamente"
        }
        failure {
            mail to: "${params.EMAIL}",
                subject: "Error al compilar el proyecto",
                body: "El proyecto no se ha compilado exitosamente"
        }
    }
}
