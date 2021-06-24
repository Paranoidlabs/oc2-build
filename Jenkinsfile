pipeline {
  agent any
  stages {
    stage('Build oc2-sedna') {
      steps {
        dir(path: 'oc2-sedna') {
          withGradle() {
            build 'build'
            build 'reobfJar'
          }

        }

      }
    }

    stage('Build oc2') {
      steps {
        dir(path: 'oc2') {
          withGradle() {
            build 'build'
            build 'reobfJar'
          }

        }

      }
    }

    stage('archive artifacts') {
      steps {
        archiveArtifacts 'oc2/build/libs/*'
        archiveArtifacts 'oc2-sedna/build/libs/*'
      }
    }

  }
}