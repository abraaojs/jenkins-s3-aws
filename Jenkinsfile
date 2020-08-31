node {
    stage('Checkout'){
        checkout scm
    }

    stage('Deploy'){
        if (env.BRANCH_NAME == 'master') {
            try {
                withAWS(region:'sa-east-1',credentials:'s3-jenkins') {
                def bucket='stg.abraaojs.com'
                //sh "aws s3 cp --recursive . s3://${bucket}/"
                //sh "aws s3 cp ${commitID()} s3://${bucket}/"
                //sh "aws s3 cp addressbook_main/target/addressbook.war s3://cloudyeticicd/"
                s3Upload(bucket:"stg.abraaojs.com", workingDir:'build', includePathPattern:'**/*');
            }
            } catch(err) {
                sh "echo error in sending artifacts to s3"
            } 
        }
        
        if (env.BRANCH_NAME == 'preprod') {
            //sh "aws s3 cp --recursive . s3://${bucket}/staging/"
            
        }
        
        if (env.BRANCH_NAME == 'develop') {
            //sh "aws s3 cp --recursive . s3://${bucket}/pre/"
        }
    }
}


 
