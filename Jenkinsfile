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

        stage ('SonarQube') {
            steps {
                 sh '''
                 mvn sonar:sonar \
                  -Dsonar.projectKey=github2 \
                  -Dsonar.host.url=http://localhost:9000 \
                  -Dsonar.login=1890805ea65026d01d5d91a5bdc52f66c42659bb
                '''
            }
        }
    }
}
