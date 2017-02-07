node("mep-lab-10") {
    stage("checkout") {
        checkout scm
        sh "env"
        sh "pwd"
        sh "ls -l"
    }

    stage("Static code check") {
        sh "pwd"
        sh "ls -l"
        //sh "./gradlew check"

        // publish Android lint result
        //androidLint canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
    }

    stage("Build in docker") {
        sh "pwd"
        sh "rm -fr app/build"
        sh "find ."
        docker.image("mingc/android-build-box:latest").inside {
            stage("Compile") {
                sh "./gradlew check build"
            }

            stage("Archive packages") {
                archive(includes: "app/build/outputs")
            }

    //        stage("Clean") {
    //            sh "./gradlew clean"
    //        }
        }
    }

    stage("Publish static analyze results") {
        // publish Android lint result
        sh "echo Publish Android lint result"
        androidLint canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
    }

    stage("Archive packages") {
        sh "find app/build/outputs"
        archive(includes: "app/build/outputs")
        //archiveArtifacts artifacts: "app/build/outputs", excludes: "app/build/outputs/logs", fingerprint: true
    }
}
