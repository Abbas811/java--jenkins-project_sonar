pipeline {
    agent any
    tools {
       maven 'maven8'
    }
    stages {
        stage("git clone"){
            steps{
                git 'https://github.com/Abbas811/java--jenkins-project_sonar.git'
            }

        }
        stage("build code"){
            steps{
                sh "mvn clean install"
        }
        }
        stage("sonar"){
            steps{
             sh 'mvn clean verify sonar:sonar \
  -Dsonar.projectKey=ak1_sonar \
  -Dsonar.host.url=http://34.230.17.68:9000 \
  -Dsonar.login=sqp_26a70f8efca0e4998f5282f53882d8cc25880f92'
        }
        }
        stage("build Docker image"){
            steps{
               sh "docker build -t abbaskhan2/works-with-heroku-2.0 ."



           }
         }
             stage("Docker deployement"){
              steps{
                 sh "docker run -d -p 8017:8080 abbaskhan2/works-with-heroku-2.0"


            }
             }



       
    }
}
