pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git 'https://github.com/IrsY/JenkinsDependencyCheckTest.git'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				script {


					sh "/var/jenkins_home/tools/org.jenkinsci.plugins.DependencyCheck.tools.DependencyCheckInstallation/OWASP_Dependency-Check_Vulnerabilities/dependency-check/dependency-check.sh \

					--project JenkinsDependencyCheckTest \

					--scan . \

					--out . \

					--format HTML \
					
					--format XML \

					--nvdApiKey df1c5439-d1ec-4d5e-ae9a-2d21c4eb2d9b"

				}
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}