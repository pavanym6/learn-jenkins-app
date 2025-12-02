pipeline {
    agent any

    stages {
        stage('build') {
            agent {
                docker {
                    image 'node: 18-alpine'
                    resueNode true

                }
            }
            steps {
                sh '''
                    "echo 'Hello Pavan"
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
