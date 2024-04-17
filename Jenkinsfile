#!/usr/bin/env groovy

pipeline {
  agent any

  stages {
    stage('Git checkout') {
      steps {
        echo 'Atualizando git'
        checkout scm
        script{
          VERSAO_POM = readMavenPom().getVersion()
        }
      }
    }
    
    stage('Compilação e testes') {
      steps {
        echo 'Compilando para verificar a correção'
        echo '${VERSAO_POM}'
      }
    }
  }
}