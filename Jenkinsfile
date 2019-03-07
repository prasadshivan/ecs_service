pipeline {
  agent any
  stages {
    stage('create service') {
      steps {
        sh 'aws ecs create-service --service-name ecs-simple-service --task-definition ExampleTask --desired-count 3'
      }
    }
   
    }
}
