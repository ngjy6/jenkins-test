pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
				echo "${env.GIT_COMMIT}"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}