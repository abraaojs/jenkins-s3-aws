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
                //sh "aws s3 cp --recursive . s3://${bucket}/prod/"
                sh "aws s3 cp ${commitID()} s3://${bucket}/"
                //s3Upload(bucket:"stgdatagate.superbid.net", workingDir:'dist', includePathPattern:'**/*');
                }
            }   
            } catch(err) {
                sh "echo error in sending artifacts to s3"
            }
        
        if (env.BRANCH_NAME == 'preprod') {
            try {
                withAWS(region:'sa-east-1',credentials:'s3-jenkins') {
                //sh "aws s3 cp addressbook_main/target/addressbook.war s3://cloudyeticicd/"
                //sh "aws s3 cp --recursive . s3://${bucket}/prod/"
                sh "aws s3 cp ${commitID()} s3://${bucket}/"
                //s3Upload(bucket:"stgdatagate.superbid.net", workingDir:'dist', includePathPattern:'**/*');
                }
            }   
            } catch(err) {
                sh "echo error in sending artifacts to s3"
            }
            
        }
        
        if (env.BRANCH_NAME == 'develop') {
          try {
                withAWS(region:'sa-east-1',credentials:'s3-jenkins') {
                //sh "aws s3 cp addressbook_main/target/addressbook.war s3://cloudyeticicd/"
                //sh "aws s3 cp --recursive . s3://${bucket}/prod/"
                sh "aws s3 cp ${commitID()} s3://${bucket}/"
                //s3Upload(bucket:"stgdatagate.superbid.net", workingDir:'dist', includePathPattern:'**/*');
                }
            }   
            } catch(err) {
                sh "echo error in sending artifacts to s3"
            }      

    }
}