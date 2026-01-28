// Filename: Jenkinsfile
node {
  def GITREPOREMOTE = "https://github.com/arnabgithubmy/Databricks.git"
  def GITBRANCH     = “main”
  def DBCLIPATH     = “/opt/homebrew/Cellar/databricks”
  def JQPATH        = " /opt/homebrew/Cellar/jq”
  def JOBPREFIX     = “jenkins_demo”
  def BUNDLETARGET  = "dev"

  stage('Checkout') {
    git branch: GITBRANCH, url: GITREPOREMOTE
  }
  stage('Validate Bundle') {
    sh """#!/bin/bash
          ${DBCLIPATH}/databricks bundle validate -t ${BUNDLETARGET}
       """
  }
  stage('Deploy Bundle') {
    sh """#!/bin/bash
          ${DBCLIPATH}/databricks bundle deploy -t ${BUNDLETARGET}
       """
  }
  
}
