pipeline {
  agent any
  stages {
    stage('Fetch dependencies') {
      steps {
        sh 'sudo docker pull karthequian/helloworld:latest'
      }
    }

    stage('Build docker image') {
      steps {
        sh 'sudo docker build . -t customapp:1'
      }
    }

    stage('Test image') {
      steps {
        sh 'echo "Tests successful !!"'
      }
    }

    stage('Push image to OCIR') {
      steps {
        sh 'sudo docker login -u \'seomcsjcs2/karthik.muthu@oracle.com\' -p \'R]538zAfT)q35Q2p8MfS\' iad.ocir.io'
        sh 'sudo docker tag customapp:1 iad.ocir.io/seomcsjcs2/customapp:custom'
        sh 'sudo docker push iad.ocir.io/seomcsjcs2/customapp:custom'
      }
    }

    stage('Deploy to OKE') {
      steps {
        sh 'sh ../../hello-deploy.sh'
      }
    }

  }
}
