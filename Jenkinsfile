pipeline {
    agent any

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
