def bucket='stgdatagate.superbid.net'

node {
    stage('Checkout'){
        checkout scm
    }

    stage('Deploy'){
        if (env.BRANCH_NAME == 'master') {
            try {
                withAWS(region:'sa-east-1',credentials:'s3-jenkins') {
                //sh "aws s3 cp addressbook_main/target/addressbook.war s3://cloudyeticicd/"
                //s3Upload(bucket:"stgdatagate.superbid.net", workingDir:'dist', includePathPattern:'**/*');
                //sh "aws s3 cp --recursive . s3://${bucket}/"
                sh "aws s3 cp ${commitID()} s3://${bucket}/"
            }
            } catch(err) {
                sh "echo error in sending artifacts to s3"
            } 
        }
        
        if (env.BRANCH_NAME == 'preprod') {
            //sh "aws s3 cp --recursive . s3://${bucket}/staging/"
            
        }
        
        if (env.BRANCH_NAME == 'develop') {
            //sh "aws s3 cp --recursive . s3://${bucket}/sandbox/"
        }
    }
}


 