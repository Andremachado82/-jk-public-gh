pipeline {
    agent any

    stages {
        stage('Clonig Git Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Andremachado82/-jk-public-gh.git'
            }
        }
        
        stage('Building Image ') {
            steps {
                sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        }
        
        stage('Deploying Application') {
            steps {
                sh '''
                # docker stop webapp_ctr
                docker run --rm -d -p 3000:3000 --name webapp_ctr webapp:${BUILD_NUMBER}                
                '''
            }
        }
    }
}
