def appName=env.APP_NAME
def gitSourceUrl=env.GIT_SOURCE_URL
def gitSourceRef=env.GIT_SOURCE_REF


pipeline {
  agent {
    label 'nodejs'
  }
  stages {

    stage('Initialize') {
      steps {
        echo "appName: ${appName}"
        echo "gitSourceUrl: ${gitSourceUrl}"
        echo "gitSourceRef: ${gitSourceRef}"
      }
    }
    stage('Checkout') {
      steps {
        echo "Checkout source."
        git url: "${gitSourceUrl}", branch: "${gitSourceRef}"
      }
    }
    stage('Build JAR') {
      steps {
        echo "Build the app."
        sh "npm build --prod"
      }
    }               
    stage('Echo output') {
      steps {
        script {
          echo "Did the build work?"
          echo "List current dir."
          sh "ls -la"
          echo "List dist dir."
          sh "ls -la dist"
        }
      }
    }
  }
}