pipeline {
  agent any
  stages {
    stage('create a new service') {
      steps {
        sh 'aws ecs create-service --cluster DevopsTest --service-name ecs-simple-service2 --task-definition ExampleTask --desired-count 3'
      }
    }
   
    }
}
