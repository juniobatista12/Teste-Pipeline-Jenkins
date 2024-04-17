#!/usr/bin/env groovy

pipeline {
  agent any

  tools{
    maven 'Maven 3.9.6'
  }

  stages {
    stage('Git checkout') {
      steps {
        echo 'Atualizando git'
        checkout scm
        script{
          VERSAO_DSPACE = readMavenPom().getVersion()
        }
      }
    }
    
    stage('Compilação e testes') {
      steps {
        echo 'Compilando para verificar a correção'
        sh "mvn clean package"
      }
    }
    stage('Construindo imagem docker'){
      steps{
        docker.build("dspace-back:${VERSAO_DSPACE}")
      }
    }
  }
}