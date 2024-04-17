#!/usr/bin/env groovy

pipeline {
  agent any

  // environment {
  //   NOME_SERVICO = 'siop'
  //   NOME_ARTEFATO = "${NOME_SERVICO}.jar"
  //   IMAGEM_DOCKER = "registry.senado.leg.br/info-doc/${NOME_SERVICO}"
  //   EMAIL_SECAO = 'equipe@senado.leg.br'
  //   NOME_REPO_MANIFESTS = "infodoc-${NOME_SERVICO}"
  //   PATH_OVERLAYS_KUSTOMIZE_TESTE = 'overlays/tes'
  //   PATH_OVERLAYS_KUSTOMIZE_PRODUCAO = 'overlays/prd'
  // }

  // tools {
  //   maven 'maven-3.8'
  //   jdk 'java-17-lts'
  // }

  stages {
    stage('Git checkout') {
      steps {
        echo 'Atualizando git'
        // checkout scm
        // scmSkip(deleteBuild: true)
        // script {
        //   VERSAO_POM = readMavenPom().getVersion()
        //   EH_VERSAO_RELEASE = !VERSAO_POM.endsWith('SNAPSHOT')
        //   //VERSAO_IMAGEM = EH_VERSAO_RELEASE ? VERSAO_POM : "${VERSAO_POM}-${env.GIT_COMMIT.take(7)}"
        //   //VERSAO_IMAGEM = EH_VERSAO_RELEASE ? VERSAO_POM : "dev"
        //   VERSAO_IMAGEM = EH_VERSAO_RELEASE ? "${VERSAO_POM}-${env.GIT_COMMIT.take(7)}" : "${VERSAO_POM}-dev"
        // }
      }
    }
    
    stage('Compilação e testes') {
      steps {
        echo 'Compilando para verificar a correção'
        // echo "Versão imagem: ${VERSAO_IMAGEM}"
        //sh "mvn -B -U -e -V clean package"
      }
    }
    
    // stage('Arquivar') {
    //   steps {
    //     //junit '**/target/surefire-reports/TEST-*.xml'
    //     archiveArtifacts "target/${NOME_ARTEFATO}"
    //   }
    // }

    // stage('Imagem Docker') {
    //   steps {
    //     echo "Versão do pom.xml: ${VERSAO_POM}. Git commit: ${env.GIT_COMMIT}"
    //     withDockerRegistry([credentialsId: 'c34117dc-5fa1-46f8-8ebb-f1cf0b2254c4', url: 'https://dockerhub.camara.leg.br/']) {
    //       script {
    //         imagem = docker.build("${IMAGEM_DOCKER}:${VERSAO_IMAGEM}")
    //         imagem.push()
    //       }
    //     }
    //   }
    // }

    // stage('Deploy Teste') {
    //   steps {
    //     patchKubernetes reponame: "${NOME_REPO_MANIFESTS}", branch: "master", path: "${PATH_OVERLAYS_KUSTOMIZE_TESTE}",
    //         kind: "Kustomize", image: "${IMAGEM_DOCKER}", tag: "${VERSAO_IMAGEM}"
    //   }
    // }

    // stage('Tag e Deploy Producao') {
    //   when {
    //     expression {
    //       return EH_VERSAO_RELEASE
    //     }
    //   }
    //   environment {
    //     NOME_TAG = "v${VERSAO_POM}"
    //   }
    //   steps {
    //     //TODO: a tag automatica de producao nao esta funcionando
    //     /*sshagent(['ssh_git']) {
    //       sh "git config user.email \"${env.EMAIL_SECAO}\""
    //       sh "git config user.name \"Jenkins\""
    //       sh "git tag -a ${NOME_TAG} -m \"Tag criada pelo Jenkins\""
    //       sh('git push --tags')
    //     }*/

    //     patchKubernetes reponame: "${NOME_REPO_MANIFESTS}", branch: "master", path: "${PATH_OVERLAYS_KUSTOMIZE_PRODUCAO}",
    //         kind: "Kustomize", image: "${IMAGEM_DOCKER}", tag: "${VERSAO_IMAGEM}"

    //     mail to: "${env.EMAIL_SECAO}",
    //       subject: "Deploy em produção - Job ${env.JOB_NAME}-${env.BUILD_DISPLAY_NAME}",
    //       body: """
    //         Foi feito deploy em produção da imagem ${IMAGEM_DOCKER}.
    //         Url do job: ${currentBuild.absoluteUrl}
    //       """
    //   }
    // }

    // //Atualizar manualmente
    // /*stage('Atualizacao da versao no pom.xml') {
    //   when {
    //     expression {
    //       return EH_VERSAO_RELEASE
    //     }
    //   }
    //   steps {
    //     script {
    //       def indiceUltimoPonto = VERSAO_POM.lastIndexOf('.')
    //       def versaoMinor = VERSAO_POM.substring(indiceUltimoPonto + 1) as Integer
    //       def proximaVersaoMinor = versaoMinor + 1
    //       PROXIMA_VERSAO = VERSAO_POM.substring(0, indiceUltimoPonto + 1) + proximaVersaoMinor + '-SNAPSHOT'
    //     }

    //     echo "Atualizando pom.xml para versão ${PROXIMA_VERSAO}"
    //     sshagent(['ssh_git']) {
    //       sh "git checkout master"
    //       sh "git pull"
    //       sh "mvn org.codehaus.mojo:versions-maven-plugin:2.5:set -DnewVersion=${PROXIMA_VERSAO} -DgenerateBackupPoms=false"
    //       sh "git add pom.xml && git commit -m \"Versão do pom atualizada para próximo SNAPSHOT\""
    //       sh "git push origin master"
    //     }
    //   }
    // }*/
  }
}
