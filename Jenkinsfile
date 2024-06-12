pipeline {
    agent any
    options {
        buildDiscarder(logRotator(daysToKeepStr: '10', numToKeepStr: '10'))
        timeout(time: 12, unit: 'HOURS')
        timestamps()
    }
    triggers {
        cron('@midnight')
    }
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your repository
                git 'https://github.com/praggya-android/DEVOPS.git'
            }
        }
        stage('Install dependencies') {
            steps {
                // Install any dependencies required for your application and tests
                sh 'pip install -r requirements.txt'
            }
        }
        stage('Run tests') {
            steps {
                // Run your unittests
                sh 'python -m unittest test_main.py'
            }
        }
    }
}
