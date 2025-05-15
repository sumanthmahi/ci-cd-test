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
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install flask
                '''
            }
        }

        stage('Run Flask App') {
            steps {
                sh '''
                    bash -c '
                        . venv/bin/activate
                        (python3 app.py > app.log 2>&1 &) && echo $! > flask.pid && disown
                    '
                '''
            }
        }
    }
}
