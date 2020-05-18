pipeline {
    agent any
    stages {
        stage('Lint HTML'){
            steps{
                sh 'tidy -q -e *.html'
            }
        }
        stage('Upload to AWS'){
            steps{
                withAWS(credentials:'aws-static') {
                    retry(2) {
                        s3Upload(bucket:"jenkins-udacity-mustafa", path:'', includePathPattern:'*.html')
                    }
                }
            }
        }
    }
}