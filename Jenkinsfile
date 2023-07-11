pipeline {
    agent any
    environment {
        name = 'Rakesh'
    }
    parameters {
        string(name: 'Person', defaultValue: 'Rakesh', description: "Who are you ?")
        booleanParam(name: 'male', defaultValue: 'true', description: "")
        choice(name: 'City', choices:['Jaipur', 'Bangalore', 'Chennai'] , description: "")
    }
    

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Run Commands') {
            steps {
                sh 'ls'
                sh 'pwd'
            }
        }
        stage('Multiple Commands') {
            steps {
                sh '''
                cal 2023
                date
                ps -ef | grep -i apache2
                '''
            }
        }
        stage('Variables') {
            environment {
                username = 'Rakesh'
            }
            steps {
                sh 'echo "${name}"'
                sh 'echo "${BUILD_ID}"'
                sh 'echo "${username}"'
            }
        }
        stage('Parameters') {
            steps {
                echo 'deploy'
                sh 'echo "${Person}"'
                sh 'echo "${name}"'
            }
        }
        stage('Continue ?') {
            input {
                message "Should we continue"
                ok "Yes Please Continue"
            }
            steps {
                echo 'deploy to prod'
            }
        }
    }
    post{
        always {
            echo 'This message for each time'
        }
        failure {
            echo 'Failure'
        }
        success {
            echo 'Success'
        }
        
    }
}
