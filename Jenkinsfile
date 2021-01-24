pipeline {
    agent any

    stages {
        stage('Compile') 
		{
            steps {
                bat './mvnw.cmd clean compile -e'
            }
            
        }
        stage('Unit') 
		{
            steps {
                bat './mvnw.cmd clean test -e'
            }
        }
      
        stage('Jar')
		{
            steps {
                bat './mvnw.cmd clean package -e'
            }
        }
       stage('SonarQube') 
		{
            steps {
                withSonarQubeEnv('sonar') //Nombre del SonarQube Server de Configurar Sistema en Jenkins 
                { // You can override the credential to be used
                    bat './mvnw.cmd org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
                }
            }
        }
	    stage('uploadNexus')
        {
            steps { 
               nexusPublisher nexusInstanceId: 'Nexus', nexusRepositoryId: 'test-nexus', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: 'jar', filePath: 'C:\\Users\\mverm\\Documents\\Repositorios\\ejemplo-maven\\build\\DevOpsUsach2020-0.0.1.jar']], mavenCoordinate: [artifactId: 'DevOpsUsach2020', groupId: 'com.devopsusach2020', packaging: 'jar', version: '0.0.1']]]
            }
       }
	    

    } //fin stages
    

} //fin pipeline
