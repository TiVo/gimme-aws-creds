@Library('tivoPipeline') _

emailBreaks {
    node('docker') {
        stage('Code Checkout'){
            checkout scm
        }
        docker.withRegistry('https://docker.tivo.com', 'docker-registry') {
            stage('Build Image') {
                def image = docker.build("docker.tivo.com/gimme-aws-creds", "-f Dockerfile --pull .")
                image.push()
            }
        }
    }
}
