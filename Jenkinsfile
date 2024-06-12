pipeline {
    agent any
    
    stages {
        stage("checkout"){
            steps {
                sh "ls"
                git branch:'main', url: 'https://github.com/denisdatsko/course3-jenkins-gs-spring-petclinic.git'
                sh "ls"
            }
        }
    
    
        stage("build"){
            steps {
                sh './mvnw package'
            }
        }
    
        stage("capture"){
            steps {
                // **/target/*.jar
                archiveArtifacts '**/target/*.jar'
                jacoco()
                junit stdioRetention: '', testResults: '**/target/surefire-reports/TEST*.xml'
            }
        }
    }
}