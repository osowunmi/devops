pipeline {
    agent {
        node {
            label 'maven-slave'
        }
    }

    stages {
        stage('build') {
            steps {
                echo "====== BUILD STARTED ======"
		sh 'mvn clean deploy -Dmaven.test.skip=true'
		echo "====== BUILD COMPLETED ======"
            }
        }
        stage('test') {
            steps {
                echo "====== UNIT TEST STARTED ======"
                sh 'mvn surefire-report:report'
                echo "====== UNIT TEST COMPLETED ======"
            }
        }
        stage('SonarQube analysis') {
	environment {
	    scannerHome = tool 'sonar_scanner'
	}
            steps {
                withSonarQubeEnv('sonar_server') {
                sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}
