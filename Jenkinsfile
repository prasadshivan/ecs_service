node {

    stage('create a new service') {
    
        /*sh 'aws ecs create-service --cluster DevopsTest --service-name ecs-simple-service2 --task-definition ExampleTask --desired-count 1'*/
        sh 'aws ecs update-service --cluster DevopsTest --service ecs-simple-service2 --task-definition ExampleTask --desired-count 1'

  
   def serviceCheckTries = 1 
   def maxThreshold = 10
   timeout(5) {
    waitUntil {
            serviceCheckTries = serviceCheckTries +1 ;
          sh 'aws ecs describe-services --cluster DevopsTest --services ecs-simple-service2 > check.json'
        def chk = readJSON file: 'check.json'
        if (serviceCheckTries == -1 && chk.services[0].deployments[0].status == 'PRIMARY' && chk.services[0].deployments[0].desiredCount == 1 && 
           chk.services[0].deployments[0].runningCount == 1) 
        
        {
       echo "Build is successful"
            return true
        }
        else if(serviceCheckTries >= maxThreshold || (chk.services[0].deployments[0].desiredCount == 0 && 
           chk.services[0].deployments[0].runningCount == 0))
        {
            echo "Buidl Error ================="
        error ("Task failed")
            
        }
        echo "Retry ==========+++++++++++++"
        return false
    }
}
        
    }
}
