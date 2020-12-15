pipeline {
    agent any

    stages {
        stage('Pipeline') {
            steps {
				script{
					def ejecucion = (params.CHOICE == 'maven') ? load 'maven.groovy' : load 'maven.groovy'
					ejecucion.call()
				}
            }
        }
    }
}
