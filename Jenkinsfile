pipeline {
  agent any
  stages {
    stage('Build oc2-sedna') {
      parallel {
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

        stage('pull gits I guess') {
          steps {
            git(url: 'https://github.com/Paranoidlabs/oc2.git', branch: '1.16.5')
            git(url: 'https://github.com/Paranoidlabs/oc2-sedna.git', branch: '1.16.4')
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