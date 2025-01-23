node {
    stage('Clone'){
	checkout scm
    }
    stage('Build image'){
	app = docker.build("kader/nginx")
    }
    stage('Run image'){
	docker.build('kader/nginx').withRun('-p 8282:82') { c ->
	sh 'docker ps'
	sh 'curl localhost'	
    }
    }
}
