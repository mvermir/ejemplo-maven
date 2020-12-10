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
       

    } //fin stages
    

} //fin pipeline
