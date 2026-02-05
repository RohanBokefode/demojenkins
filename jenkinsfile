pipeline {
    agent any

    environment {
        NAME = 'ROHAN'
    }

    parameters {
        string(
            name: 'Person',
            defaultValue: 'Rohan Bokefode',
            description: 'Who are you'
        )

        booleanParam(
            name: 'isMale',
            defaultValue: true,
            description: ''
        )

        choice(
            name: 'city',
            choices: ['Pune', 'Mumbai', 'Delhi'],
            description: 'Select your city'
        )
    }

    stages {

        stage('Run A command') {
            steps {
                sh '''
                    ls
                    date
                    pwd
                '''
            }
        }

        stage('Environment Variables') {
            environment {
                USERNAME = 'Myusername'
            }
            steps {
                sh 'echo "BUILD_ID = ${BUILD_ID}"'
                sh 'echo "USERNAME = ${USERNAME}"'
                sh 'echo "GLOBAL NAME = ${NAME}"'
            }
        }

        stage('Parameters') {
            steps {
                sh '''
                    echo "Person : ${Person}"
                    echo "isMale : ${isMale}"
                    echo "City   : ${city}"
                '''
            }
        }

        stage('Continue ?') {
            steps {
                input message: 'Should we continue?', ok: 'Yes we should'
            }
        }

        stage('Deploy on prod') {
            steps {
                echo 'Deploy on prod'
            }
        }
    }
  post {
    always {
        echo 'This always runs'
    }
    success {
        echo 'Pipeline succeeded'
    }
    failure {
        echo 'Pipeline failed'
    }
}

}
