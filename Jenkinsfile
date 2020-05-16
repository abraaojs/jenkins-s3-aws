def bucket='stgdatagate.superbid.net'

node {
    stage('Checkout'){
        checkout scm
    }

    stage('Deploy'){
        if (env.BRANCH_NAME == 'master') {
            //sh "aws s3 cp --recursive . s3://${bucket}/"
            sh "aws s3 cp ${commitID()} s3://${bucket}/"
        }
        
        if (env.BRANCH_NAME == 'preprod') {
            //sh "aws s3 cp --recursive . s3://${bucket}/staging/"
            sh "aws s3 cp ${commitID()} s3://${bucket}/"

            
        }
        
        if (env.BRANCH_NAME == 'develop') {
            //sh "aws s3 cp --recursive . s3://${bucket}/sandbox/"
            sh "aws s3 cp ${commitID()} s3://${bucket}/"

        }
    }
}