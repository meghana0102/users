users(jenkinsfile)
   pipeline{
    agent {
        label 'NODEJS'
    }
    stages {
        stage('Compile Code') {
            steps {
                sh '''
                mvn compile
            '''
            }
        }
        stage('Make Package') {
            steps {
                sh '''
                mvn package
            '''
            }
        }
        stage('prepare Artifacts') {
            steps {
                sh '''
                zip -r users.zip *
            '''
            }
        }
        stage('upload Artifacts') {
            steps {
                sh '''
           curl -f -v -u admin:Mega@3103 --upload-file users.zip http://172.31.4.60:8081/repository/users/users.zip
        '''
            }
        }
    }
}