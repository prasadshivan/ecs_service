node {

    stage('create a new service') {
    
        /*sh 'aws ecs create-service --cluster DevopsTest --service-name ecs-simple-service2 --task-definition ExampleTask --desired-count 1'*/
        sh 'aws ecs update-service --cluster DevopsTest --service ecs-simple-service2 --task-definition ExampleTask --desired-count 1'

  

   timeout(5) {
    waitUntil {
          sh 'aws ecs describe-services --cluster DevopsTest --services ecs-simple-service2 > check.json'
        def chk = readJSON file: 'check.json'
        echo "********* start"
        echo chk.toString()
        echo "********* end"
        echo "Statusvalue ::::::::: ${chk.services[0].deployments[0].status}"
        return chk.services[0].deployments[0].status == 'ACTIVE'
       
    }
}
        
    }
}

        
  





