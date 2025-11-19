pipeline {
    agent any
    environment {
        // Setting JAVA_HOME and PATH for Unix (Linux)
        // JAVA_HOME = "/usr/bin/java"
        // JAVA_HOME = 'C:\\Program Files\\Java\\jdk-17'
        JAVA_HOME= "\$( if isUnix() then /usr/bin/java else C:\\Program Files\\Java\\jdk-17 fi )"
        //PYTHON_HOME= "/usr/bin/python3"
        // PYTHON_HOME = 'C:\\Users\\green\\AppData\\Local\\Programs\\Python\\Python313'
        PYTHON_HOME = "\$(if isUnix() then /usr/bin/python3 else  C:\\Users\\green\\AppData\\Local\\Programs\\Python\\Python313 fi)"
        //PATH = "${env.PATH}:${JAVA_HOME}/bin:/usr/bin:${PYTHON_HOME}" 
        // PATH="${env.PATH};${JAVA_HOME}\\bin;${PYTHON_HOME}"
        PATH = "\$(if isUnix() then  \${env.PATH}:\${JAVA_HOME}/bin:/usr/bin:\${PYTHON_HOME}  else  \${env.PATH};\${JAVA_HOME}\\bin;\${PYTHON_HOME} fi)"
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
                            bat 'python hello.py'                            
                    }
                }
            }
        }
    }
}
