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

    environment {
        PATH = "$HOME/Library/Python/3.9/bin:$PATH"
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Boonkai/jenkins.git', branch: 'main'
            }
        }

        stage('Install') {
            steps {
                sh '''
                    python3 -m pip install --upgrade pip
                    pip3 install --user pytest
                    if [ -f requirements.txt ]; then pip3 install --user -r requirements.txt; fi
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    echo "PATH during Test: $PATH"
                    pytest -v --maxfail=1 --disable-warnings -q --junitxml=pytest.xml
                '''
            }
        }
    }

    post {
        always {
            junit 'pytest.xml'
        }
    }
}
