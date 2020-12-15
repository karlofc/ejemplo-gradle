pipeline {
    agent any

    stages {
        stage('Pipeline') {
            steps {
				script{
					def ejecucion = load 'maven.groovy'
					ejecucion.call()
				}
            }
        }
    }
}
