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
	    stage('Build') {
    	    steps {
    	    sh "mvn --version" //shellscript
    	    //sh "node --version"
    	    sh "docker version"
              echo "Build"
              echo "$PATH - $PATH"
              echo "BUILD_NUMBER - $env.BUILD_NUMBER"
              echo "JOB_NAME - $env.JOB_NAME"
              echo "BUILD_TAG - $env.BUILD_TAG"
              echo "BUILD_URL - $env.BUILD_URL"
    	    }
    	}
  	    stage('Test') {
      	    steps {
                  echo "Test"
      	    }
      	}
	    stage('Integration Test') {
    	    steps {
                echo "Integration Test"
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