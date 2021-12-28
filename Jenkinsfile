pipeline {
    agent any
    stages {
        stage('Example Username/Password') {
            steps {
                sh '''#!/bin/bash
                echo "Service user is"
                curl -o menu.pdf https://www.marinabaysands.com/content/dam/revamp/restaurants/restaurant-details/black-tap/menus/BT-Menu.pdf
                pwd
                ls -l
                '''
            }
        }
    }
}
