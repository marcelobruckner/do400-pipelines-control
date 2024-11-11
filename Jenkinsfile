node('nodejs') {
    stage('Checkout') {
        git branch: 'main', 
        url: 'https://github.com/marcelobruckner/do400-pipelines-control'
    }

    stage('Backend Tests') {
        sh 'node ./simple-webapp/backend/test.js'
    }

    stage('Frontend Tests') {
        sh 'node ./simple-webapp/frontend/test.js'
    }
}