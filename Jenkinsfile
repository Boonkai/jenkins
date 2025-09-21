// pipeline {
//     agent any

//     stages {
//         stage('Checkout') {
//             steps {
//                 git branch: 'main', url:'https://github.com/Boonkai/jenkins.git'
//             }
//         }

//         stage('Build') {
//             steps {
//                 echo 'Building...'
//             }
//         }

//         stage('Test') {
//             steps {
//                 sh 'python3 --version'
//                 sh 'python3 script.py'
//             }
//         }

//         stage('Deploy') {
//             steps {
//                 echo 'Deploy step (placeholder)'
//             }
//         }
//     }
// }

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                 git branch: 'main', url:'https://github.com/Boonkai/jenkins.git'
            }
        }

        stage('Install') {
            steps {
                sh 'python3 -m pip install --upgrade pip'
                sh 'pip3 install -r requirements.txt || true'
            }
        }

        stage('Test') {
            steps {
                sh 'pytest -v --maxfail=1 --disable-warnings -q'
            }
        }
    }

    post {
        always {
            junit '**/pytest.xml'
        }
    }
}
