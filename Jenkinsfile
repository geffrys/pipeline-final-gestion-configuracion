pipeline {
    agent any
    
    stages {
        
        stage('Build') {
            steps {
                // Configurar Maven
                tool 'Maven'
                // Ejecutar el comando de construcción de Maven
                sh 'mvn clean install'
            }
        }
        stage('Send mail'){
            steps{
                mail to: 'geffry.ospina@gmial.com'
                subject: 'Build Success'
                body: 'The build was successful'
        }
        
    }
}