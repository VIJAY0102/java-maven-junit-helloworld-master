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
	}
	
	post {
		always{
			 node('master') {
  				      		sh'''
        					echo 'Hello, world!'
        					'''
        					logstashSend failBuild: true, maxLines: -1
				 }
		}
	}
}
