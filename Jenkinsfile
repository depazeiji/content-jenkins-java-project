pipeline{
  agent any

  stages{
    stage('build'){
      steps{
        sh 'ant -f build.xml -v'
      }
    }
  }

  post{
    always{
      archiveArtifacts artifacts: 'dist/*.jar', fingerprint: true
      emailext(
            subject: "${env.JOB_NAME} [${env.BUILD_NUMBER}] Development Promoted to Master",
            body: """<p>'${env.JOB_NAME} [${env.BUILD_NUMBER}]' Development Promoted to Master":</p>
            <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>""",
            to: "depazeiji@gmail.com"
          )
    }
  }
}
