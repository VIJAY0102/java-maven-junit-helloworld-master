pipeline {
	agent any
	
	stages {
		stage("Build") {
			steps {
				echo '---Build started----!'
				git 'https://github.com/jeydevops/java-maven-junit-helloworld.git'
				sh 'mvn clean package -DskipTests=true'
				//logstashSend failBuild: true, maxLines: 1000
			}
		}
		
		stage("Testing") {							
			steps {
			 echo 'Unit Tests Are Awesome!'
       sh 'mvn test'
			}
		}
		
		stage("Send ConsoleLog to Logstash") {
			steps {
				echo '---Archive jenkins Console Logs to Elasticsearch----!'				
				logstashSend failBuild: true, maxLines: 1000
			}
		}
	
	}
}
