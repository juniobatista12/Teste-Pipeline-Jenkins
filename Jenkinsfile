#!/usr/bin/env groovy

pipeline {
  agent any

  stages {
    stage('Git checkout') {
      steps {
        echo 'Atualizando git'
      }
    }
    
    stage('Compilação e testes') {
      steps {
        echo 'Compilando para verificar a correção'
      }
    }
  }
}