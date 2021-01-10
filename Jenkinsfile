pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''echo PATH = ${PATH}
echo M2_HOME = ${M2_HOME}

mvn -clean'''
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