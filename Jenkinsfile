#!groovy

stage 'Compile'
node {
    checkout scm
    // use for non multibranch: git 'https://github.com/amuniz/maven-helloworld.git'
    def mvnHome = tool 'maven-3'

    sh "${mvnHome}/bin/mvn clean install -DskipTests"

    stash 'working-copy'
}

stage 'Test'
node {
    unstash 'working-copy'

    def mvnHome = tool 'maven-3'
    sh "${mvnHome}/bin/mvn test"

}