pipeline {
    agent {
        node {
            label 'maven-slave'
        }
    }

    stages {
        stage('build') {
            steps {
                sh 'mvn clean deploy'
            }
        }
    }
}
