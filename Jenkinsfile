pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                echo 'Cloning repo...'
            }
        }

        stage('Set Up Python') {
            steps {
                sh '''
                    sudo apt-get update
                    sudo apt-get install -y python3.12-venv
                    python3 -m venv venv
                    . venv/bin/activate
                    pip3 install flask
                '''
            }
        }

        stage('Run Flask App') {
            steps {
                sh '''#!/bin/bash
                    set -e
                    source venv/bin/activate
                    setsid python3 app.py --host=0.0.0.0 --port=5000 > app.log 2>&1 < /dev/null &
                '''
            }
        }
    }
}
