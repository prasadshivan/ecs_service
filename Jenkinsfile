pipeline {
  agent any
  stages {
    stage('create a new services') {
      steps {
        sh 'aws ecs create-service --cluster DevopsTest --service-name ecs-simple-service --task-definition ExampleTask --desired-count 3'
      }
    }
   
    }
}
