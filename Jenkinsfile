pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage ('Initial') {
            steps {
              sh '''
                   echo "PATH = ${PATH}"
                   echo "M2_HOME = ${M2_HOME}"
               '''
            }
        }

        stage ('Compile') {
            steps {
                 sh 'mvn clean compile -e'
            }
        }

        stage ('Test') {
            steps {
                 sh 'mvn clean test -e'
            }
        }

        stage ('SonarQube') {
            steps {
                 sh '''
                 mvn sonar:sonar \
                  -Dsonar.projectKey=Maven \
                  -Dsonar.host.url=http://172.18.0.3:9000 \
                  -Dsonar.login=4b5f68e7a9670ae20e30e3212a570651245647c6
                '''
            }
        }

        stage ('SCA') {
            steps {
                 echo 'sca'
            }
        }

        stage ('JAR Create') {
            steps {
                 sh 'mvn clean package -e'
            }
        }

        stage ('Run JAR ') {
            steps {
                 sh 'mvn spring-boot:run'
                 //curl -X GET 'http://localhost:8081/rest/mscovid/test?msg=testing'
            }
        }



    }
}
