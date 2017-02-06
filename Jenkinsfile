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
        androidLint canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
    }

    //stage("Build in docker") {
    //    sh "pwd"
    //    sh "ls -l"
    //    docker.image("mingc/android-build-box:latest").inside {
    //        stage("Compile") {
    //            sh "./gradlew build"
    //        }
    //
    //        stage("Archive packages") {
    //            archive(includes: "app/build/outputs")
    //        }
    //
    //        stage("Clean") {
    //            sh "./gradlew clean"
    //        }
    //    }
    //}
}
