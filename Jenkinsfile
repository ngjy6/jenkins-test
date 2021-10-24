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
					env.GIT_COMMIT_MSG = sh (script: '"C:/Program Files/Git/bin/git.exe" log -1 --pretty=%B ${GIT_COMMIT}', returnStdout: true).trim()
					env.GIT_AUTHOR = sh (script: '"C:/Program Files/Git/bin/git.exe" log -1 --pretty=%cn ${GIT_COMMIT}', returnStdout: true).trim()
					env.GIT_LAST_COMMIT_USER = sh (script: '"C:/Program Files/Git/bin/git.exe" log -1 --pretty=format:"%an"', returnStdout: true).trim()
				}
				
				echo "Git commit message: ${env.GIT_COMMIT_MSG}"
				echo "Git author: ${env.GIT_AUTHOR}"
				echo "Git last commit user: ${env.GIT_LAST_COMMIT_USER}"
				
				echo "Env job name: ${env.JOB_NAME}"
				echo "Env job base name: ${env.JOB_BASE_NAME}"
				echo "Env branch name: ${env.BRANCH_NAME}"
				echo "Env workspace: ${env.WORKSPACE}"
				echo "Env workspace temp: ${env.WORKSPACE_TMP}"
				
				
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