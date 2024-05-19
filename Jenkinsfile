
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
        stage('Clone repository') {
            steps {
                sh "git clone ${params.GITHUB_URL}"
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
    }
}
