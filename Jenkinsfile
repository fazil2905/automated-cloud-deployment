pipeline {
    agent any

    environment {
        IMAGE = "fazil2905/devops-app"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t %IMAGE%:latest .'
            }
        }

        stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'docker-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    bat '''
                    echo %DOCKER_PASS%>pass.txt
                    type pass.txt | docker login -u %DOCKER_USER% --password-stdin
                    del pass.txt
                    '''
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                bat 'docker push %IMAGE%:latest'
            }
        }

        stage('Terraform Init') {
            steps {
                dir('terraform') {
                    bat 'terraform init'
                }
            }
        }

        stage('Terraform Apply (Deploy to ECS)') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'aws-creds',
                    usernameVariable: 'AWS_ACCESS_KEY_ID',
                    passwordVariable: 'AWS_SECRET_ACCESS_KEY'
                )]) {
                    dir('terraform') {
                        bat '''
                        set AWS_ACCESS_KEY_ID=%AWS_ACCESS_KEY_ID%
                        set AWS_SECRET_ACCESS_KEY=%AWS_SECRET_ACCESS_KEY%
                        terraform apply -auto-approve
                        '''
                    }
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}