pipeline {
      options {
        // This is required if you want to clean before build
        skipDefaultCheckout(true)
    }
environment {
imagename = "theironhidex/hello-world"
registryCredential = 'dockerHubAccount'
dockerImage = ''
}
agent any
stages {
stage('Cloning Git') {
steps {
git([url: 'https://github.com/TheIronhidex/devops-repo.git', branch: 'main', credentialsId: 'gitHubAccount'])
}
}
          stage('Build') {
            steps {
                // Clean before build
                cleanWs()
                // We need to explicitly checkout from SCM here
                echo "Building ${env.JOB_NAME}..."
            }
        }
    /*
stage('Building image') {
steps{
script {
dockerImage = docker.build imagename
}
}
}
stage('Deploy Image') {
steps{
script {
docker.withRegistry( '', registryCredential ) {
dockerImage.push("$BUILD_NUMBER")
}
}
}
}
stage('Remove Unused docker image') {
steps{
sh "docker rmi $imagename:$BUILD_NUMBER"
}
}
*/
}
}
