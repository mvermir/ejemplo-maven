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
               bat 'nexusPublisher nexusInstanceId: 'nexus-dev2', nexusRepositoryId: 'test-nexus', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: 'jar', filePath: 'C:\Users\Miguel\Documents\repositoriosDevOps\fork_def\ejemplo-maven\build\DevOpsUsach2020-0.0.1.jar']], mavenCoordinate: [artifactId: 'spring-boot-starter-parent', groupId: 'org.springframework.boot', packaging: 'jar', version: '0.0.1']]], tagName: '0.0.1''
            }
       }
       

    } //fin stages
    

} //fin pipeline
