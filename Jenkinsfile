node {
        stage('scm'){
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/MarinaBoboshko/testapp.git/']]])
        }
        stage('Build image') {
                sh """
                docker ps
                """
        dir('app'){
                def app = docker.build("myname")
                def workspace = docker.build.getEnvVars()["WORKSPACE"]

        }

    }
         stage('Test image') {
         dir('app'){
                sh """
                docker ps
                pwd
                ls
                """
                sh """
                echo workspace

                """
}
         }



}
