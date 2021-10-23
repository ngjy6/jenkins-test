pipeline {
    agent any
	
	environment {
		PATH = "C:\\Program Files\\Git\\bin"
	}

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
				echo "Git commit: ${env.GIT_COMMIT}"
				
				script {
				    pwd
					env.GIT_COMMIT_MSG = sh (script: 'git log -1 --pretty=%B ${GIT_COMMIT}', returnStdout: true).trim()
				}
				
				echo "Git commit message: ${env.GIT_COMMIT_MSG}"
				
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