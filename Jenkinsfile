pipeline {
    agent any
    stages {
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