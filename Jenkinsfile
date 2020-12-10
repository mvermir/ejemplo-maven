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
	    

    } //fin stages
    

} //fin pipeline
