#!groovy



stage('Compile') {
    node {
        checkout scm
        // use for non multibranch: git 'https://github.com/amuniz/maven-helloworld.git'
        def _mvnHome = tool 'M3'
        sh "${_mvnHome}/bin/mvn -B -Dmaven.test.failure.ignore verify"

        sh "${_mvnHome}/bin/mvn clean install -DskipTests"

        stash 'working-copy'
    }
}

stage ('Test') {
    node {
        unstash 'working-copy'
        def _mvnHome = tool 'M3'
        sh "${_mvnHome}/bin/mvn test"
    }
}
