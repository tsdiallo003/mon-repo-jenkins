def gv

pipeline {
  agent any
  parameters {
    string(name: 'VERSION', defaultValue: '', description: 'version to deploye')
    choice(name: 'VERSION', choices: ['1.1', '1.2', '1.3'], description: 'version à deployer')
    booleanParam(name: 'executeTests', defaultValue: true, description: 'ok')
  }
  stages {
    stage('prepare') {
      steps {
        script{
          gv = load "script.groovy"
        }
      }
    }
    stage("build") {
      steps {
        gv.build()
      }
    }
    
    stage("test") {
      when {
        expression  {
          params.executeTests
        }
      }
      steps {
        gv.testApp()
      }
    }
    
    stage("deploy") {
      steps {
        gv.deployeApp()
      }
    }
  
  }

}
