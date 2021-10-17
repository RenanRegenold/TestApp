def gv

pipeline {
    agent any
    parameters {
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }

//    tools {
//        gradle 'Gradle-6.2'
//    }
    stages {
        stage("init") {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }

        stage("build") {
            steps {
                script {
                    gv.buildApp()
                }
            }
        }

        stage("test") {
            when {
                expression {
                    params.executeTests
                }
            }
            steps {
                script {
                    gv.testApp()
                }
            }
        }

        stage("deploy") {
            steps {
                script {
                    gv.deployApp()
                }
            }
        }

    }
//        stage("run frontend") {
//            steps {
//                echo 'executing yarn...'
//                nodejs('Node-10.17') {
//                    sh 'yarn install'
//                }
//            }
//        }
//        stage("run backend") {
//            steps {
//                echo 'executing gradle...'
//                sh './gradlew -v'                
//            }
//        }
}
