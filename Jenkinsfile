pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'this is a minimal pipeline'
      }
    }

    stage('Browser Test') {
      parallel {
        stage('Firefox') {
          steps {
            git(url: 'https://github.com/dikabrenda/JenkinsPipeline', branch: 'pipeline')
          }
        }

        stage('Chrome') {
          steps {
            git(url: 'https://github.com/dikabrenda/JenkinsPipeline', branch: 'pipeline', changelog: true)
          }
        }

        stage('Edge') {
          steps {
            git(url: 'https://github.com/dikabrenda/JenkinsPipeline', branch: 'pipeline', changelog: true)
          }
        }

        stage('Safari') {
          steps {
            git(url: 'https://github.com/dikabrenda/JenkinsPipeline/', branch: 'pipeline')
          }
        }

      }
    }

    stage('Reports') {
      steps {
        junit 'Target-Surefire-reports/**/*.xml'
      }
    }

    stage('Deploy') {
      steps {
        archiveArtifacts 'target/*.jartarget/*.hpi'
      }
    }

  }
}