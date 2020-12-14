pipeline {
    agent any

    stages {
        stage('Pipeline') {
            steps {
				script{
					stage('build & test'){
					    bat 'gradle clean build'
					}
					stage('sonar'){
					    def scannerHome = tool 'sonar-scanner';
						withSonarQubeEnv('sonar') {
							bat "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=ejemplo-gradle -Dsonar.java.binaries=build -Dsonar.login=75a0e9b0613f563c0e69a23174cf79eb5d4d74c7"
						}
					}
					stage('run'){
					}
					stage('testing'){
					}
					stage('nexus'){
					}
				}
            }
        }
    }
}