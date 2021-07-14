pipeline {
  agent any
  tools {
    maven 'my_maven'
  }
  stages {
    stage("Compile") {
      steps { sh "mvn compile" }
    }
    stage("Unit test") {
      steps { sh "mvn test" }
    }
  }
  post {
    always {
    step([$class: 'JacocoPublisher',
           execPattern: 'target/*.exec',
	   classPattern: 'target/classes',
	   sourcePattern: 'src/main/java',
	   exclusionPattern: 'src/test*'])
    }
  }
}

