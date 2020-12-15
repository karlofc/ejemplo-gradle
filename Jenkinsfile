pipeline {
    agent any

    stages {
        stage('Pipeline') {
            steps {
				script{
					def ejecucion = (params.CHOICE == 'maven') ? load 'maven.groovy' : load 'gradle.groovy'
					ejecucion.call()
				}
            }
        }
    }
}
