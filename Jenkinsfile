//Scripted pipeline approach
//node {
//	stage('Build') {
//		echo "Build"
//	}
//	stage('Test') {
//		echo "Test"
//	}
//	stage('Integration Test') {
//    	echo "Integration Test"
//    }
//}

// Declarative pipeline approach
pipeline {
    agent any
    //agent { docker {image "maven:3.6.3"}}
    //agent { docker {image "node:13.8"}}
    environment {
        dockerHome = tool "myDocker"
        mavenHome = tool "myMaven"
        PATH = "$dockerHome/bin:$mavenHome/bin:$PATH" // Adding environment variables to the image path
    }
    stages {
	    stage('Checkout') {
    	    steps {
    	        sh "mvn --version" //shell script
    	        //sh "node --version"
    	        sh "docker version"
              echo "Build"
              echo "PATH - $PATH"
              echo "BUILD_NUMBER - $env.BUILD_NUMBER"
              echo "JOB_NAME - $env.JOB_NAME"
              echo "BUILD_TAG - $env.BUILD_TAG"
              echo "BUILD_URL - $env.BUILD_URL"
    	    }
    	}
    	stage('Compile') {
    	    steps{
    	        sh "mvn clean compile"
         	}
    	}
  	    stage('Unit Test') {
      	    steps {
                sh "mvn test"
      	    }
      	}
	    stage('Integration Test') {
    	    steps {
                sh "mvn failsafe:integration-test failsafe:verify"
    	    }
        }
    }

    post {
        always {
            echo "Always running."
        }
        success {
             echo "Only when success."
        }
        failure {
            echo "Only when failed."
        }
        //changed {} if the status of a build changed.
    }
}