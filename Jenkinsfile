node {

    stage('create a new service') {
    
        /*sh 'aws ecs create-service --cluster DevopsTest --service-name ecs-simple-service2 --task-definition ExampleTask --desired-count 1'*/
        sh 'aws ecs update-service --cluster DevopsTest --service ecs-simple-service2 --task-definition ExampleTask --desired-count 1 > service.json'
    }    
        stage ('status check'){
        def srvc = readJSON file: 'service.json'
        def ids = srvc.service.deployments[0].id
        echo ids
        sh 'aws ecs describe-services --cluster DevopsTest --services ecs-simple-service2 > build.json'
        def bld = readJSON file: 'build.json'
        def idb = bld.service.deployments[0].id

        if ids == idb {
        def status == 'PRIMARY'

        while status == 'PRIMARY' {
        sh 'aws ecs describe-services --cluster DevopsTest --services ecs-simple-service2 > check.json'
        def chk = readJSON file: 'check.json'
        status == chk.service.deployments[0].status
        }


        }
        else {
          build failed
        }

        }

    }




