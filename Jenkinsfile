pipeline {
    agent any

    tools {
        nodejs 'NodeJS 18' // Ensure NodeJS is configured in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/charlesantonysamyu/sample-react-app.git', branch: 'master'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Deploy') {
            steps {
                sh 'cp -r build/* /opt/tomcat/webapps/ROOT/'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed. Cleaning up workspace.'
            deleteDir()
        }
    }
}
