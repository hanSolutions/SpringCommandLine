#!groovy

def _mvnHome = tool 'M3'

stage('Compile') {
    node {
        checkout scm
        // use for non multibranch: git 'https://github.com/amuniz/maven-helloworld.git'

        sh "${_mvnHome}/bin/mvn -B -Dmaven.test.failure.ignore verify"

        sh "${_mvnHome}/bin/mvn clean install -DskipTests"

        stash 'working-copy'
    }
}

stage ('Test') {
    node {
        unstash 'working-copy'

        sh "${_mvnHome}/bin/mvn test"
    }
}