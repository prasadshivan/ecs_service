node {

    stage('create a new service') {
    
        /*sh 'aws ecs create-service --cluster DevopsTest --service-name ecs-simple-service2 --task-definition ExampleTask --desired-count 1'*/
        sh 'aws ecs update-service --cluster DevopsTest --service ecs-simple-service2 --task-definition ExampleTask --desired-count 1'

        timeout(120) {
    waitUntil {

        sh 'aws ecs describe-services --cluster DevopsTest --services ecs-simple-service2 > check.json'
        def chk = readJSON file: 'check.json'
        sh 'cat check.json'
        def status = 'Active'
        chk.services.deployments[0].status = status
    }
}

        
  }

}



