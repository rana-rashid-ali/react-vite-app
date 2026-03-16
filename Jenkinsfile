pipeline {
    agent any

    environment {
        VERCEL_TOKEN = credentials('vercel-token')
       
    }

    stages {

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

      stage('Test') {
            steps {
                echo "skipping tests. no test script found'
            }
        }
        stage('Build Project') {
            steps {
                bat 'npm run build'
            }
        }

        stage('Deploy to Vercel') {
            steps {
                bat 'npx vercel --prod --yes --token=$VERCEL_TOKEN
                vercel deploy --prebuilt --prod --token=$VERCEL_TOKEN
                '''
            }
        }
    }

    post {
        success {
            echo "Deployment Successful!"
        }
        failure {
            echo "Pipeline Failed!"
        }
    }
}
