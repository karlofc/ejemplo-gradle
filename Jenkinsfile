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
}
