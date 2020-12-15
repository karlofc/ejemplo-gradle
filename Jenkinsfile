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
						bat 'start gradle bootRun'
					}
					stage('testing'){
						sleep 10
						bat 'curl http://localhost:8082/rest/mscovid/estadoMundial'
					}
					stage('nexus'){
						nexusPublisher nexusInstanceId: 'nexus', nexusRepositoryId: 'test-nexus', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: 'C:\\Users\\carlo.figueroa\\.jenkins\\workspace\\_multibranch_feature-dir-inicial\\build\\libs\\DevOpsUsach2020-0.0.1.jar']], mavenCoordinate: [artifactId: 'DevOpsUsach2020', groupId: 'com.devopsusach2020', packaging: 'jar', version: '1.0.0']]]
					}
				}
            }
        }
    }
}