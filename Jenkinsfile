pipeline {
    agent any

	parameters {
        choice(name: 'CHOICE', choices: ['maven', 'gradle'], description: 'Herramienta de construccion')
    }

    stages {
        stage('Pipeline') {
            steps {
				script{
					def build = (params.CHOICE == 'maven') ? 'maven.groovy' : 'gradle.groovy'
					def ejecucion = load build
					ejecucion.call()
				}
            }
        }
    }
	post {
        success {
            slackSend channel: 'dipdevopsusach2020', color: 'good', message: 'Build Success: [Carlo Figueroa][${env.JOB_NAME}][${params.CHOICE}] Ejecución exitosa."', tokenCredentialId: 'slack-token-diplomado'
        }
        failure {
            slackSend channel: 'dipdevopsusach2020', color: 'danger', message: 'Build Failure: [Carlo Figueroa][${env.JOB_NAME}][${params.CHOICE}] Ejecución fallida en stage []."', tokenCredentialId: 'slack-token-diplomado'
        }
    }
}
