pipeline {
    agent any

    environment {
        IMAGE_NAME = "jeevanshettya/my_react_app"
        DOCKERHUB = credentials('dockerhub')
    }

    stages {

        stage('Checkout') {
    steps {
        git branch: 'main',
            url: 'https://github.com/1ms24mc037-Jeevan/my_react_app.git'
    }
}


        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:latest .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker login -u $DOCKERHUB_USR -p $DOCKERHUB_PSW'
                sh 'docker push $IMAGE_NAME:latest'
            }
        }
    }

    post {
        success {
            echo "React Manual Pipeline Successful"
        }
	  failure{
		echo "React Manual Pipeline Successful"
	  }
        always {
            cleanWs()
        }
    }
}
