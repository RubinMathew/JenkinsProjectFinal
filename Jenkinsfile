pipeline {
  agent any
  stages {
    stage('CodeCollection') {
      steps {
        git(url: 'https://github.com/RubinMathew/simpleMavenJunit.git', branch: 'master', changelog: true, poll: true)
      }
    }

    stage('Compile') {
      steps {
        node(label: 'slave1') {
          sh '''mvn clean
mvn compile
'''
        }

      }
    }

    stage('Test') {
      steps {
        node(label: 'slave2') {
          sh 'mvn test'
        }

      }
    }

  }
}