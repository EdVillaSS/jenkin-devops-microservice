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
    stages {
	    stage('Build') {
    	    steps {
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
    }
}