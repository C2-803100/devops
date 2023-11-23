pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/C2-80310/devops.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_AMX9gqNYbdcMsPdCgSUtHa1JAd0 | /usr/bin/docker login -u ankush1996 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t ankush1996/mywebsite .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push ankush1996/mywebsite'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm myservice1'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name myservice1 -p 9090:80 --replicas 5 ankush1996/mywebsite'
            }
        }
    }
}

