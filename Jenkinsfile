pipeline {
    agent any

    environment {
        COMPOSE_PROJECT_NAME = 'bank-project'
        DOCKERHUB_CREDENTIALS = credentials('docker-hub-credentials')  // 옵션, 나중에 쓰고 싶으면
        GIT_COMMIT_HASH = ''
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo "📥 GitHub에서 소스 가져오는 중..."
                checkout scm
            }
        }

        stage('Docker Compose Build') {
            steps {
                echo "🔨 docker-compose build 실행 중..."
                sh 'docker-compose build'
            }
        }
    }

    post {
        success {
            echo '✅ Docker 이미지 빌드 완료!'
        }
        failure {
            echo '❌ 빌드 실패! 로그를 확인하세요.'
        }
    }
}