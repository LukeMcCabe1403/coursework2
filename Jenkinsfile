node {
    def app

    stage('clone repository'){

    
        checkout scm
    }

    stage('Build image') {

    app = docker.build("lmccabe1403/courseworkimage")

    }

    stage('Test Image') {

    app.inside {
        echo "Tests passed"
    }

    }

    stage('Push image'){

    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {   

    app.push("${env.BUILD_NUMBER}")
    app.push("latest")
    }

     echo "Trying to push docker build to dockerhub"
}
}
