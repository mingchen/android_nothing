node {
    stage("checkout") {
        checkout scm
        sh "pwd"
        sh "ls -l"
    }

    stage("Static code check") {
        sh "./gradlew check"

        // publish Android lint result
        androidLint canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
    }

    stage("Build in docker") {
        docker.image("mingc/android-build-box:latest").inside {
            stage("Compile") {
                sh "./gradlew build"
            }

            stage("Archive packages") {
                archive(includes: "app/build/outputs")
            }

            stage("Clean") {
                sh "./gradlew clean"
            }
        }
    }
}
