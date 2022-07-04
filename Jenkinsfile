pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "MyMaven"
    }

    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/sharadrajore/spring-boot-demo.git'

              

                // To run Maven on a Windows agent, use
                 bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }

          
        }
        
         stage('Deploy') {
            steps {
               deploy adapters: [tomcat8(credentialsId: 'tomcat-cred', path: '', url: 'http://localhost:9090/')], contextPath: null, onFailure: false, war: '**/*.war'
            }

          
        }
    }
}
