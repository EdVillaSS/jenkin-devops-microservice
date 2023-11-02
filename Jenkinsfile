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
    //agent any
    agent { docker {image "maven:3.6.3"}}
    stages {
	    stage('Build') {
    	    steps {
    	    sh "mvn --version" //shellscript
                echo "Build"
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