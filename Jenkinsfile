pipeline {
    agent any
    environment {
        // Setting JAVA_HOME and PATH for Unix (Linux)
        JAVA_HOME = isUnix() ? '/usr/bin/java' : 'C:\\Program Files\\Common Files\\Oracle\\Java\\javapath\\java.exe'
        PYTHON_HOME= isUnix() ? '/usr/bin/python3' : 'C:\\Users\\green\\AppData\\Local\\Microsoft\\WindowsApps\\python3.exe'
        PATH = isUnix() ? "${env.PATH}:${JAVA_HOME}/bin:/usr/bin:${PYTHON_HOME}" : "${env.PATH};${JAVA_HOME}\\bin;C:\\Users\\green\\AppData\\Local\\Microsoft\\WindowsApps\\python3.exe"
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/achenouda/testJenkins.git'
            }
        }
        stage('Build') {
            steps {
                script {
                    if (isUnix()) {
                            sh 'echo "Running on Unix"'
                            sh 'java HelloWorld.java'
                            sh 'python3 hello.py'
                        }
                     else {
                         
                            bat 'echo "Running on Windows"'
                            bat 'javac HelloWorld.java'
                            bat 'java HelloWorld'
                            bat 'python hello.py'
                    }
                }
            }
        }
    }
}
