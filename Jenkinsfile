pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout main branch
                git branch: 'main', url: 'https://github.com/NikolaiDimitro/SEDO-Exam-Prep-2-2.git'
            }
        }

        stage('Build & Test (main only)') {
            when {
                expression {
                    // Проверяваме текущия branch
                    env.GIT_BRANCH == 'origin/main' || env.GIT_BRANCH == 'main'
                }
            }
            steps {
                bat "dotnet restore"
                bat "dotnet build --no-restore"
                bat "dotnet test --no-build --verbosity normal"
            }
        }
    }
}