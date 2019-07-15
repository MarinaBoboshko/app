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

        }

    }
         stage('Test image') {
         dir('app'){
                sh """
                docker run -t myname
              //  docker exec -t friendly_elion cat text.txt > Data.txt
                docker ps
                pwd
                ls
                cat text.txt
                """
}
         }



}
