pipeline {
    agent any

    stages {

        stage("Build & Test (main only)") {
            when {
                expression {
                    env.GIT_BRANCH?.endsWith('main')
                }
            }

            stages {

                stage("Restore") {
                    steps { bat "dotnet restore" }
                }

                stage("Build") {
                    steps { bat "dotnet build" }
                }

                stage("Test") {
                    steps { bat "dotnet test" }
                }
            }
        }
    }
}