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
         appcontainer.inside('-v/var/run/docker.sock:/var/run/docker.sock '){
                sh """
                python app/app.py
                cat text.txt
                cp text.txt /var/lib/jenkins/workspace/app/textnew.txt

                """
         }
         stage ('Test Data'){
          sh " cat textnew.txt"
         }
         
         }


}
