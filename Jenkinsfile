pipeline {
    agent any
    environment {
        // Setting JAVA_HOME and PATH for Unix (Linux)
        // JAVA_HOME = "/usr/bin/java"
        JAVA_HOME = "\$( if isUnix() then /usr/bin/java else C:\\Program Files\\Java\\jdk1.8.0_202 fi )"
        //PYTHON_HOME= "/usr/bin/python3"
        PYTHON_HOME = "\$(if isUnix() then /usr/bin/python3 else  C:\\Users\\green\\AppData\\Local\\Microsoft\\WindowsApps\\python3.exe fi)"
        //PATH = "${env.PATH}:${JAVA_HOME}/bin:/usr/bin:${PYTHON_HOME}" 
        PATH="\$(if isUnix() then  \${env.PATH}:\${JAVA_HOME}/bin:/usr/bin:\${PYTHON_HOME}  else  \${env.PATH};\${JAVA_HOME}\\bin;C:\\Users\\green\\AppData\\Local\\Microsoft\\WindowsApps\\python3.exe fi)"
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
                            bat 'java HelloWorld'
                            bat 'python hello.py'
                    }
                }
            }
        }
    }
}
