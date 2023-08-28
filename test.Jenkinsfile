pipeline {
    agent { 
        docker {
            image 'devtools.mlp.de/shared/build/build-maven:3.9.1-eclipse-temurin-17-focal-10'
            args '-v /root/.m2:/root/.m2'
        }

    }
    stages {
        stage("Clean Up"){
            steps {
                deleteDir()
            }
        }
        stage("Clone Repo"){
            steps {
                sh "git clone  https://github.com/jenkins-docs/simple-java-maven-app.git"
            }
        }
        stage("Build") {
            steps {
                dir("simple-java-maven-app") {
                    sh "mvn clean install"
                }
            }
        }
        stage("Test") {
            steps {
                dir("simple-java-maven-app") {
                    sh "mvn test"
                }
            }          
        }
    }
}
