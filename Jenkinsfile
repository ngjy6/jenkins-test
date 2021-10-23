pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
				echo "Git commit: ${env.GIT_COMMIT}"
				
				script {
					env.GIT_COMMIT_MSG = sh (script: 'git log -1 --pretty=%B ${env.GIT_COMMIT}', returnStdout: true).trim()
					env.GIT_AUTHOR = sh (script: 'git log -1 --pretty=%cn ${env.GIT_COMMIT}', returnStdout: true).trim()
				}
				
				echo "Git commit message: ${env.GIT_COMMIT_MSG}"
				
				echo "Git author: ${env.GIT_AUTHOR}"
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