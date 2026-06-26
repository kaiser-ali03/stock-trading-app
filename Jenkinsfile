 pipeline{
    agent any
    environment{
        BUILD_CONFIG = 'release'
    }
    stage("checkout"){
        steps{
            checkout scm
        }
    }
    stage("restore"){
        steps{
            sh 'dotnet restore'
        }
    }
    stage("build"){
        steps{
            sh 'dotnet build --configuration $BUILD_CONFIG'
        }
    }
    stage("test"){
        steps{
            sh 'dotnet test --no-build'
        }
    }

    stage("publish"){
        steps{
            sh 'dotnet publish --configuration $BUILD_CONFIG -o publish'
        }
    }

    stage("archive"){
        steps{
            sh 'archiveArtifacts artifact: 'publish/**, fingerprint:true'
        }
    }
}
