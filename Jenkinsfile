node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update dep') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        sh 'cat yaml/and.yaml'
                        sh    "sed -i 's/wapp.*/prg3:${DOCKERTAG2}/g' yaml/and.yaml"   
                        sh 'cat yaml/and.yaml'
                        sh "git add ."
                        sh "git commit -m 'X ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/ufst.git HEAD:main"
      }
    }
  }
}
}
