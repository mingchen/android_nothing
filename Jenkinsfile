pipeline {
    agent {
        docker {
            image: "mingc/android-build-box:latest"
            //label: "mep-lab-10"
        }
    }

    stages {
        stage("checkout") {
            checkout scm
            sh "env"
            sh "pwd"
            sh "ls -l"
        }

        stage("Compile") {
            sh "./gradlew check build"
        }

        stage("Publish static analyze results") {
            // publish Android lint result
            sh "echo Publish Android lint result"
            androidLint canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
        }

        stage("Archive packages") {
            archive(includes: "app")
            //archive(includes: "app/build/outputs")
            //archiveArtifacts artifacts: "**/app/build/outputs", excludes: "**/app/build/outputs/logs"
        }
    }
}
