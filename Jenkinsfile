pipeline{
    agent any 
    tools{
        maven "maven3.9.9"
    }

    stages{
        stage('clone from scm'){
            steps{
                sh "echo jenkins to clone from scm"
                git branch: 'april5', url: 'https://github.com/Onomeing/liontech-online-library-web-app.git'

            }
        }

        stage('maven build'){
            steps{
                sh "echo 'running junit test on the source code'"
                sh "echo 'maven to build and package the source code'"
                sh "mvn install"
                sh "mvn verify"
                sh "mvn test"
                sh "mvn validate"
                sh "mvn clean package"
            }
        }

        //stage ('code inspection'){
            //steps{
                //sh "echo 'sonarqube to perform code quality inspection'"
                //sh "mvn sonar:sonar"
            //}
        //}

            stage('upload to artifact'){
            steps{
                sh "echo 'deploy artifact to nexus'"
                sh "mvn deploy"
            }
        }
          stage('deploying to production'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'TOMCAT-CRED2', path: '', url: 'http://13.58.90.241:8009/manager/html')], contextPath: 'demo-1', war: 'target/*.war'
            }
        }
    }    
}    