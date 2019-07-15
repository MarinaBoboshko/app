node {
        stage('scm'){
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/MarinaBoboshko/testapp.git/']]])
        }
        stage('Build image') {
                sh """
                docker ps
                """
        dir('app'){
                appcontainer = docker.build("myname")

        }

    }
         stage('Test image') {
         dir('app'){
                sh """
                docker ps
                pwd
                ls
                """
}
         }
         stage ('Testing container'){
         appcontainer.inside('-v /git/test/app/ : /test/app/ '){
                sh "ls"
                sh "pwd"
         }
         }


}
