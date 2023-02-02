pipeline {
  agent any
  parameters {
    string(name: 'VERSION', defaultValue: '', description: 'version to deploye')
    choice(name: 'VERSION', choices['1.1', '1.2', '1.3'], description: 'version à deployer')
    booleanParam(name: 'executeTests', defaultValue: true, description: 'ok')
  }
  stages {
    stage("build") {
      steps {
        echo '************BUILD*************'
      }
    }
    
    stage("test") {
      when {
        expression  {
          params.executeTests
      }
      steps {
        echo '************TEST*************'
      }
    }
    
    stage("deploy") {
      steps {
        echo '************DEPLOY*************'
        echo 'deploying ${params.VERSION}'
      }
    }
  
  }

}
