node {

    stage('create a new service') {
    
        /*sh 'aws ecs create-service --cluster DevopsTest --service-name ecs-simple-service2 --task-definition ExampleTask --desired-count 1'*/
        sh 'aws ecs update-service --cluster DevopsTest --service ecs-simple-service2 --task-definition ExampleTask --desired-count 1'

  

   timeout(5) {
    waitUntil {
       script {
          sh 'aws ecs describe-services --cluster DevopsTest --services ecs-simple-service2 > check.json'
        def chk = readJSON file: 'check.json'
        def status = 'ACTIVE'
          echo status
           chk.services.deployments[0].status = "${status};
       }
    }
}
}
}

        
  





