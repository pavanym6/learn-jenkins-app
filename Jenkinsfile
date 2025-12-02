pipeline {
    agent any

    stages {
        stage('build') {
            agent {
                docker {
                    image 'node:18-alpine'               
                    reuseNode true

                }
            }
            steps {
                sh '''
                    echo "Hello Pavan"
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
        stage ('Test'){
            steps {
                
                sh '''
                    echo "Test stage"
                    test -d build
                    echo "build exists"
                    npm test
                '''
            }
        }
    }
}
