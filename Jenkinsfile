pipeline {
    agent any

    stages {
        stage('clone-repo') {
            steps {
               git 'https://github.com/nageshvkn/gamutkart2.git' 
            }
        }
         stage('build') {
            steps {
               sh 'mvn install -Dmaven.test.skip=true' 
            }
        }
        stage('test-unit') {
            steps {
               sh 'mvn install' 
            }
        }
        stage('deployment') {
            steps {
               sh 'sshpass -p "ram" scp target/gamutgurus.war ram@172.17.0.3:/home/ram/apache-tomcat-9.0.59/webapps'
               sh 'sshpass -p "ram" ssh ram@172.17.0.3 "/home/ram/apache-tomcat-9.0.59/bin/startup.sh"'
            }
        }
    }
}

