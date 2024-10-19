pipeline{
    agent any
    stages{
        stage('checkout the code from github'){
            steps{
                 git url: 'https://github.com/mhanumesh07/CICD_Banking_Finance/'
                 echo 'github url checkout'
            }
        }
        stage('CODE COMPILE'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('CODE TESTING'){
            steps{
                sh 'mvn test'
            }
        }
        stage('Q&A'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('PACKAGE'){
            steps{
                sh 'mvn package'
            }
        }
        stage('RUN DOCKERFILE'){
          steps{
               sh 'docker build -t myimg .'
           }
         }
        stage('PORT EXPOSE'){
            steps{
                sh 'docker run -dt -p 8091:8091 --name c000 myimg'
            }
        }   
    }
}
