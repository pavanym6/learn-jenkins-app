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
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                
                sh '''
                    echo "Test stage"
                    if [ -d "build" ]; then
                        echo "build exists"
                        npm test
                    else
                        echo "build does not exist" 
                        exit 1
                    fi                  
                    
                '''
            }
        }
    }
}
