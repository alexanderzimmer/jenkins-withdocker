node {
    def app
    stage('Checkout') {
        checkout scm
    }
    stage('Build') {
        app = docker.build("alexzimmer/jenkins-withdocker")
    }
    stage('Publish') {
        withRegistry('https://registry.hub.docker.com', '79de71d8-4d7a-44c8-a6e9-55e43269ff34') {
            app.push("lts")
            app.push("latest")
        }
    }
}
