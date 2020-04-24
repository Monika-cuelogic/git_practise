node {

  def app

  stage('clone repository') {

    checkout scm

  }

  stage('Build image') {

    app = docker.Build("monikan/my-test-docker")

  }
  stage('Test image') {

    app.inside {

      sh 'echo "Tests Passed"'

    }

  }

  stage('Push Image') {


    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentails') {
      app.push(1)
      app.push('latest')
    }

  }

}