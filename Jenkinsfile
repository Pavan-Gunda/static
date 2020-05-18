pipeline {
    agent any
    stages {
        stage('Lint HTML'){
            steps{
                sh 'echo Linting HTML'
                sh 'tidy -q -e *.html'
            }
        }
        stage('Upload to AWS'){
            steps{
                withAWS(credentials:'aws-static') {
                    retry(2) {
                        s3Upload(bucket:"bulbulu", path:'', includePathPattern:'*.html')
                    }
                }
            }
        }
    }
}