pipeline{
    agent any

    triggers {
        pollSCM('* * * * *')
    }

    stages {
        stage('Checkout'){
            steps {
                git branch: 'master',
                url: 'https://github.com/LeeHyeonHo-127/jenkins_webapp'
            }
        }

        stage('Build'){
            steps {
                sh 'mvn package -Dmaven.test.skip=true'
            }
        }

        stage('Test'){
            steps {
                sh 'mvn test'
            }
        }

        stage('Deploy'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat_manager', url: 'http://192.168.56.102:8080')], contextPath: null, war: 'target/hello-world.war'
            }
        }
    }
}

