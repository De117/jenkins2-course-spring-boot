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
}
