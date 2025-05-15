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
                    pip install flask
                '''
            }
        }

        stage('Run Flask App') {
            steps {
                sh '''                    
                    . venv/bin/activate
                    nohup python3 app.py > app.log 2>&1 &
                '''
            }
        }
    }
}
