
node {
  stage('checkout sources') {
        // You should change this to be the appropriate thing
        //git url: 'https://github.com/ColumbusStateWorkforceInnovation/special-topics-ci-lab'
        git url: 'https://github.com/esaboleyjr/specialtopics-ci-lab'
  }

  stage('Build') {
    // you should build this repo with a maven build step here
    withMaven (maven: 'maven3') {
      sh "mvn package"
    }
    echo "hello"
  }
  // you should add a test report here

  node {
      try {
          stage('Test') {
              sh './gradlew check'
          }
      } finally {
          archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
          junit 'build/reports/**/*.xml'
      }
  }
}
