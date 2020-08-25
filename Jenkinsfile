pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "Maven"
    }

    stages {
        stage('Verify') {
            steps {
                sh "mvn -v"
            }
        }
        stage('Compile') {
            steps {
                sh "mvn clean compile"
            }
        }
        stage('Test') {
            steps {
                sh "mvn test"
            }
            
            post {
                always{
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
    
    post {
        success {
            discordSend description: 'Success (Gaëlle)', 
            footer: '', 
            image: '', 
            link: '', 
            result: 'SUCCESS', 
            thumbnail: '', 
            title: '', 
            webhookURL: 'https://discordapp.com/api/webhooks/747819422705778738/dHWPHidlNLpiiKftWU84__Ss2LAkws77Swfdk5OWs22qla3hlI1B4zywW8ROg4nAwjRM'
        }

        failure {
            discordSend description: 'Échec (Gaëlle)', 
            footer: '', 
            image: '', 
            link: '', 
            result: 'FAILURE', 
            thumbnail: '', 
            title: '', 
            webhookURL: 'https://discordapp.com/api/webhooks/747819422705778738/dHWPHidlNLpiiKftWU84__Ss2LAkws77Swfdk5OWs22qla3hlI1B4zywW8ROg4nAwjRM'
        }

    }
}
