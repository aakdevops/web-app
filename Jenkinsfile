pipeline {
    agent {
	docker 'openjdk:8-jre'
    }
    stages {
        stage('test') {
            steps {
                echo 'hello! this is beta branch build test going on. You will see java version next.'
		sh 'java -version'
            }
        }
    }
}
