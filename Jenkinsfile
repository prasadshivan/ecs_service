node {

    stage('create a new service') {
    
        /*sh 'aws ecs create-service --cluster DevopsTest --service-name ecs-simple-service2 --task-definition ExampleTask --desired-count 1'*/
        sh 'aws ecs update-service --cluster DevopsTest --service ecs-simple-service2 --task-definition ExampleTask --desired-count 1'
    




        /*def srvc = readJSON file: 'service.json'
        def ids = srvc.service.deployments[0].id;
        echo "${ids}"
        sh 'aws ecs describe-services --cluster DevopsTest --services ecs-simple-service2 > build.json'
        sh 'cat build.json'
        def bld = readJSON file: 'build.json'
        def idb = bld.services.deployments[0].id;
        echo "${idb}"

        status = 'PRIMARY'

        while (status == 'PRIMARY') { */
        
        
        

        timeout(120) {
    waitUntil {

        sh 'aws ecs describe-services --cluster DevopsTest --services ecs-simple-service2 > check.json'
        def chk = readJSON file: 'check.json'
        chk.services.deployments[0].status = 'ACTIVE'
    }
}

        
  }

}



