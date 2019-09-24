node {
    stage 'Clone repository'
    checkout([
        $class: 'GitSCM',
        branches: [
            [name: '*/master']
        ],
        doGenerateSubmoduleConfigurations: false,
        extensions: [],
        submoduleCfg: [],
        userRemoteConfigs: [
            [url: 'https://github.com/De117/jenkins2-course-spring-boot']
        ]
    ])

    stage 'Build & package'
    def img = docker.build('atmosphere-jenkins')

    stage 'Push Docker image to ECR'
    docker.withRegistry(
        // My AWS registry URI:
        // (You'll want to fill in yours)
        'https://473293451041.dkr.ecr.eu-central-1.amazonaws.com',
        // My ECR credentials:
        // (Format is 'ecr:region:id-of-credentials-in-jenkins')
        'ecr:eu-central-1:614a2de1-e751-44c1-9713-0a3a8b4a5ef6'
   ) {
        img.push('latest')
   }
}
