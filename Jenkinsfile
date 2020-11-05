pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                dir('java-tomcat-sample/') {
    sh 'mvn -f pom.xml clean package'
}
               
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Deploy in Staging Environment'){
            steps{
                build job: 'Deploy2'

            }
            
        }
        stage('Deploy to Production'){
            steps{
                timeout(time:5, unit:'DAYS'){
                    input message:'Approve PRODUCTION Deployment?'
                }
                build job: 'deploy production'
            }
        }
    }
}
