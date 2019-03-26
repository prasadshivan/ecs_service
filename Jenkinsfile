pipeline {
  agent any
  stages {
    stage('create a new service') {
      steps {
        /*sh 'aws ecs create-service --cluster DevopsTest --service-name ecs-simple-service2 --task-definition ExampleTask --desired-count 1'*/
        sh 'aws ecs update-service --cluster DevopsTest --service ecs-simple-service2 --task-definition ExampleTask --desired-count 1'

      }
    }
    stage('Check status of task') {
      steps {
        sh 'aws ecs describe-services --services ecs-simple-service2 > build.json'
        sh 'cat build.json'

      }

    }

   
    }
}
