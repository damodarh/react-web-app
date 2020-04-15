pipeline
{
  agent any
  
  tools
  {
    nodejs 'node'
  }
  
  stages
  {
    stage('Stage One')
    {
      steps
      {
          script
        {
          cleanWs()
          checkout changelog: false, poll: false, scm: [$class: 'GitSCM', branches: [[name: '${RepoBranch}']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/damodarh/react-web-app.git']]]
          sh '''
          ls -ltr
          npm install
          npm run build
          cd build/
          ls -ltr
          tar -cvf frontend-${BUILD_NUMBER}.tar *
          '''
        }
      }
    }
  }
}
