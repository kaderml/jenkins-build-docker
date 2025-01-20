node {
    stage('Clone'){
        git 'https://github.com/kaderml/jenkins-helloworld.git'
    }
    stage('Build'){
       sh ' javac Main.java'
    }
    stage('Run'){
        sh ' java Main'
    }
}
