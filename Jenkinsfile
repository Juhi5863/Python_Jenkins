

pipeline {

    agent any

    stages {

        stage('Clone Repository') {

            steps {

                git branch: 'main', url: 'https://github.com/Juhi5863/Python_Jenkins.git'

            }

        }

       
            stage('Run Code'){
                steps {
                    sh 'python3 juhi.py'
                }
            }

    }

}
