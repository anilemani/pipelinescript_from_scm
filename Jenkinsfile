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
               sh 'sshpass -p "syam" scp target/gamutgurus.war syam@172.17.0.4:/home/syam/apache-tomcat-9.0.59/webapps'
               sh 'sshpass -p "syam" ssh syam@172.17.0.4 "/home/syam/apache-tomcat-9.0.59/bin/startup.sh"'
            }
        }
    }
}

