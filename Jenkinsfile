node {

    stage('create a new service') {
    
        /*sh 'aws ecs create-service --cluster DevopsTest --service-name ecs-simple-service2 --task-definition ExampleTask --desired-count 1'*/
        sh 'aws ecs update-service --cluster DevopsTest --service ecs-simple-service2 --task-definition ExampleTask --desired-count 1 > service.json'
        def srvc = readJSON file: 'service.json'
        def idp = srvc.service.deployments[0].id
        echo idp
        sh 'aws ecs describe-services --cluster DevopsTest --services ecs-simple-service2 > build.json'
        sh 'cat build.json'
    }
    

    }

