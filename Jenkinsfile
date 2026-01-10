pipeline {
    agent{
        image 'node:'
    }
    stages {
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh'''
                    ls -la
                    node --version
                    npm --version
                    npm ci 
                    npm run build
                    ls -la
                '''
            }
        }
        stage('Test'){
            when{
                expression { return fileExists('build/index.html')}
            }
            steps{
                sh'''
                    echo "Test Stage"
                    npm --version
                '''
            }
        }
    }
}
