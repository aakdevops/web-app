pipeline{
	agent any
	stages{
		stage('build') {
			steps{
				sh 'docker build -t aaakash/webapp:1 .'
			}
		}
		stage('test') {
			steps{
				sh 'docker run --name webapp1 -p 80:80 -d aaakash/webapp:1'
				def resp = sh(returnStdout: true,
                                        script: """
                                                set +x
                                                curl -w "%{http_code}" -o /dev/null -s \
                                                http://\"${contport}\"
                                                """
                                        ).trim()
                if ( resp == "200" ) {
                        println "tutum hello world is alive and kicking!
                        currentBuild.result = "SUCCESS"
			}
                     else {
                        println "Nginx failed to start"
                        currentBuild.result = "FAILURE"

			}
	}
}
}
}

