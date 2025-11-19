pipeline {
    agent any
    environment {
        // Setting JAVA_HOME and PATH for Unix (Linux)
        // JAVA_HOME = "/usr/bin/java"
        JAVA_HOME = 'C:\\Program Files\\Java\\jdk-17'
        //PYTHON_HOME= "/usr/bin/python3"
        PYTHON_HOME = 'C:\\Users\\green\\AppData\\Local\\Microsoft\\WindowsApps'
        //PATH = "${env.PATH}:${JAVA_HOME}/bin:/usr/bin:${PYTHON_HOME}" 
        PATH="${env.PATH};%JAVA_HOME%\bin;%PYTHON_HOME%"
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
                            bat 'echo %JAVA_HOME%'
                            bat 'echo %PYTHON_HOME%'
                            bat 'echo %PATH%' 
                            bat 'java.exe HelloWorld.java'
                            bat 'python3 hello.py'                            
                    }
                }
            }
        }
    }
}
