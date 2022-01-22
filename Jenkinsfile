pipeline{
    agent any
        
        
    stages{
        stage('Checkout'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], 
                extensions: [], userRemoteConfigs: [[credentialsId: 'github-cred', 
                url: 'https://github.com/badhekomal17/Jenkins22012022.git']]])
            }
        }
        
        stage('Build'){
            steps{
                bat 'mvn clean package'
            }
        }
        
        stage('Deploy'){
            steps{
                deploy adapters: [tomcat8(credentialsId: 'tomcat-cred', path: '', 
                url: 'http://localhost:8080/')], contextPath: null, 
                war: '**/*.war'
            }
        }
    }
}