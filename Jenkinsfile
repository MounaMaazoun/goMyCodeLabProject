pipeline{
    agent any 
    stages {
        stage("Clone repository") {
            steps {
                echo "Clone repository"
                checkout scm
                // script {
                //     env.MY_GIT_TAG = sh(returnStdout: true, script: "git tag -l --points-at HEAD")
                // }
                
                echo "hello ${env.BUILD_NUMBER}"
            }
        }
        stage("build front-end ") {
            steps {
                echo "building the angular-app"
                sh 'docker build -f ./angular-app/Dockerfile -t angular-app:${BUILD_NUMBER} ./angular-app'
            }
        }
       stage("build backend-end ") {
            steps {
                echo "building the express-server"
                sh 'docker build -f ./express-server/Dockerfile -t express-server:${BUILD_NUMBER} ./express-server'
            }
        }
    }

}