pipeline {
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
}
}
