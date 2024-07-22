pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				//git '/home/JenkinsDependencyCheckTest'
                echo 'checking out scm'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '''
                --format HTML --format XML 
                --nvdApiKey 550b31ae-58e2-43ce-a0cb-cf545144548a
                --suppression suppression.xml
                ''', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}