//Note: you can set your own vars ex: CODE_CHANGES == getCodeChanges() == getCodeChanges would be a script to check code changes

pipeline {
    agent any

    //Example of declaring your own env vars
    environment {
        CURRENT_VERSION = '1.1'
    }

    paramters{
        choice(name: 'Type', choices: ['Small', 'Medium', 'Large'], description: 'Size')
    }
    
    stages {
        stage("Build") {
            when {
                expression {
                    //Example cont. (See note at top) CODE_CHANGES == true
                }
            }
            steps {
                echo "Building version: ${CURRENT_VERSION}"
                echo 'Building the App...'
            }
        }
        stage("Test") {
            when {
                expression {
                    //env.BRANCH_NAME == 'dev'
                    BRANCH_NAME == 'dev' || BRANCH_NAME == 'main'
                }
            }
            steps {
                echo 'Testing the App...'
            }
        }
        stage("Deploy") {
            steps {
                echo 'Deploying the App...'
            }
        }
    }
    //post {
        //always {
            //Always to do this post stages
       // }

        //success {
            //Do this after all stages successfully done
        //}

        //failure {
            //Do this if build has a failure
        //}
    //}
}
