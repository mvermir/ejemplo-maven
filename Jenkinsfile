pipeline {
    agent any

    stages {
           stage('Compile') {
            steps {
            dir('C:\\Users\\Miguel\\Desktop\\ejemplo-maven-main')
             {
                bat './mvnw.cmd clean compile -e'
             }
            
           }
        }

            stage('Unit') {
            steps {
            dir('C:\\Users\\Miguel\\Desktop\\ejemplo-maven-main')
            {
                bat './mvnw.cmd clean test -e'
            }
          }
      }

            stage('Jar') {
            steps {
             dir('C:\\Users\\Miguel\\Desktop\\ejemplo-maven-main')
             {
                bat './mvnw.cmd clean package -e'
            }
          }
        }

             stage('Run') {
            steps {
             dir('C:\\Users\\Miguel\\Desktop\\ejemplo-maven-main')
             {
                bat 'start mvnw.cmd spring-boot:run'
                
             }

          }
        }

        stage('Test') {
            steps {
             dir('C:\\Users\\Miguel\\Desktop\\ejemplo-maven-main')
             {
                sleep 20 
               bat 'curl http://localhost:8081/rest/mscovid/test?msg=testing'
            }
         } 

       }
       

   
    }

}