node {
    def app
    stage('Checkout') {
        checkout scm
    }
    stage('Build') {
        app = docker.build("alexzimmer/jenkins-withdocker")
    }
    stage('Publish') {
            withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: '79de71d8-4d7a-44c8-a6e9-55e43269ff34', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD']]) { 
            sh "docker login --username=${USERNAME} --password=${PASSWORD}"
            app.push("lts")
            app.push("latest")
        }
    }
}
