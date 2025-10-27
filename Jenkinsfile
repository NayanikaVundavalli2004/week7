pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Building Docker image..."
                bat "docker build -t mypythonflaskapp ."
            }
        }
        stage('Run') {
            steps {
                echo "Running container..."
                bat "docker rm -f mycontainer || true"
                bat "docker run -d -p 5050:5000 --name mycontainer mypythonflaskapp"
            }
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs.'
        }
    }
}
