pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/Harshada1344/practice.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_WH-CqdmWs2bLAioMe5YyUf7C-bQ | /usr/bin/docker login -u harshada437 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t harshada437/practice .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push harshada437/practice'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm practice'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name practice -p 4000:4000 --replicas 2 harshada437/practice'
            }
        }
    }
}
