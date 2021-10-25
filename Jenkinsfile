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
					env.LS = sh (script: 'ls -l', returnStdout: true).trim()
					
					env.REPO_NAME = sh(script: 'echo $(basename ${GIT_URL%.git})', returnStdout: true)
					echo "Git repo name: ${env.REPO_NAME}"
					
				}
				
				echo "Git commit message: ${env.GIT_COMMIT_MSG}"
				echo "Git author: ${env.GIT_AUTHOR}"
				echo "Git last commit user: ${env.GIT_LAST_COMMIT_USER}"
				
				echo "Env job name: ${env.JOB_NAME}"
				echo "Env job base name: ${env.JOB_BASE_NAME}"
				echo "Env branch name: ${env.BRANCH_NAME}"
				echo "Env workspace: ${env.WORKSPACE}"
				echo "Env workspace temp: ${env.WORKSPACE_TMP}"
				
				echo "Env LS: ${env.LS}"
				
				
            }
        }
        stage('Test') {
            steps {
                echo 'Pylint..'
		sh '''#!/bin/bash
			"C:/Users/STARLORD/AppData/Local/Programs/Python/Python37/python3.exe" -m venv ~/.somevenv
			source "C:/Users/STARLORD/AppData/Local/Programs/Python/Python37/.somevenv/bin/activate"
			"C:/Users/STARLORD/AppData/Local/Programs/Python/Python37/Scripts/pip.exe" install --upgrade pip &&\
  			"C:/Users/STARLORD/AppData/Local/Programs/Python/Python37/Scripts/pip.exe" install -r requirements.txt
			touch __init__.py
			"C:/Users/STARLORD/AppData/Local/Programs/Python/Python37/python3.exe" -m pylint --output-format=parseable
		'''
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
