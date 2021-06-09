pipeline {
    agent any
    tools { 
        maven 'Maven'
    }
    stages {
        stage ('Compile') {
            steps {
                sh '''
                    ./mvnw clean compile -e
                ''' 
            }
        }

        stage ('Build') {
            steps {
                echo 'This is a minimal pipeline.'
            }
        }
    }
}
