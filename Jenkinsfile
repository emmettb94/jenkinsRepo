//Note: you can set your own vars ex: CODE_CHANGES == getCodeChanges() == getCodeChanges would be a script to check code changes

def gv //Global var for script

pipeline {
    agent any

    //Example of declaring your own env vars
    environment {
        CURRENT_VERSION = '1.1'
    }

    parameters{
        choice(name: 'TYPE', choices: ['Small', 'Medium', 'Large'], description: 'Size')
    }
    
    stages {

        stage("init") {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }
        
        stage("Build") {
            //when {
            //    expression {
                    //Example cont. (See note at top) CODE_CHANGES == true
            //    }
            //}
            steps {
                echo "Building version: ${CURRENT_VERSION}"
                script {
                    gv.buildApp()
                }
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
                echo "Deploying the App... ${params.TYPE}"
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
