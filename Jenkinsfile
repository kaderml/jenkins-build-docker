node {
    stage('Clone') {
        checkout scm
    }
    stage('Build image') {
        app = docker.build("kader/nginx")
    }
    stage('Run image') {
        app.withRun('-p 8383:80') { c ->
            sh 'docker ps'
            sh 'curl localhost:8383'
        }
    }
}
