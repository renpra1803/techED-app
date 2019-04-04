@Library('piper-library-os') _

node() {

  stage('prepare') {

      checkout scm

      setupCommonPipelineEnvironment script:this

           checkChangeInDevelopment script: this,changeDocumentId:'8000004822'
       }

  stage('build') {
      mtaBuild script: this
  }

  stage('neoDeploy') {
      neoDeploy script: this
  }

  stage('solmanUpload') {
      transportRequestCreate script:this,developmentSystemId: 'SM1~ABAP/001',changeDocumentId:'8000004822'
      transportRequestUploadFile script:this,changeDocumentId:'8000004862',transportRequestId:'SM1K900475',applicationId: 'HCP'
  }
}
