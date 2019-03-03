pipeline {
         agent any
         stages {
                 stage('Checkout') {
                 steps {
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'PerBuildTag'], [$class: 'CheckoutOption']], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'd9e07ca4-fd91-4bde-8f57-f14a36844f3e', url: 'https://github.com/JithinSivan/hello-world-spring-boot.git']]])
                 }

                 }
                 stage('Two') {
                 steps {
                    input('Do you want to proceed?')
                 }
                 }
                 stage('Three') {
                 when {
                       not {
                            branch "master"
                       }
                 }
                 steps {
                       echo "Hello"
                 }
                 }
                 stage('Four') {
                 parallel {
                            stage('Unit Test') {
                           steps {
                                echo "Running the unit test..."
                           }
                           }
                            stage('Integration test') {
                              agent {
                                    docker {
                                            reuseNode true
                                            image 'ubuntu'
                                           }
                                    }
                              steps {
                                echo "Running the integration test..."
                              }
                           }
                           }
                           }
              }
}