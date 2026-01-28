node {
  def GITREPOREMOTE = "https://github.com/arnabgithubmy/Databricks.git"
  def GITBRANCH     = "main"
  def JOBPREFIX     = "jenkins_demo"
  def BUNDLETARGET  = "dev"

  // Ensure Homebrew bin is on PATH for this node
  env.PATH = "/opt/homebrew/bin:${env.PATH}"

  stage('Checkout') {
    git branch: GITBRANCH, url: GITREPOREMOTE
  }

  stage('Validate Bundle') {
    sh """#!/bin/bash
          set -e
          which databricks || { echo "databricks not found on PATH"; exit 1; }
          databricks --version
          databricks bundle validate -t ${BUNDLETARGET}
       """
  }

  stage('Deploy Bundle') {
    sh """#!/bin/bash
          set -e
          databricks bundle deploy -t ${BUNDLETARGET}
       """
  }
}
