pipeline {
  agent any
  stages {
    stage('Register new Task Defenition') {
      steps {
        sh 'aaws ecs create-service --service-name ecs-simple-service --task-definition ExampleTask --desired-count 3'
      }
    }
   
    }
}
