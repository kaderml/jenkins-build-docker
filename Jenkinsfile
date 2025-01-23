node {
    def registryProjet='registry.gitlab.com/kaderml/jenkins' 
    def IMAGE="${registryProjet}:version-${env.BUILD_ID}"
    
    stage ('Clone') {
       git branch: 'main', url: 'https://github.com/kaderml/jenkins-build-docker.git'
    }
    
    def img = stage ('Build') {
       docker.build("$IMAGE", '.')
    }
    
    stage ('Run') {
        img.withRun("--name run-$BUILD_ID -p 87:80") { c ->
            sh 'sleep 10' // Attendre que Nginx démarre
            sh 'docker logs run-$BUILD_ID' // Afficher les logs du conteneur
            sh 'curl localhost:87'
        }
    }
    stage('Push') {
        docker.withRegistry ('https://registry.gitlab.com', 'reg1') {
            img.push 'latest' 
            img.push()
        }
    }
}
