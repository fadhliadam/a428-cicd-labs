node{
    withDockerContainer(args: '-p 3000:3000', image: 'node:16-buster-slim'){
        stage('Build') {
            sh 'npm install'
        }
        stage('Test') { 
            sh './jenkins/scripts/test.sh' 
        }
        stage('Manual Approval') {
            input message: 'Lanjutkan ke tahap Deploy? (Klik "Proceed" untuk melanjutkan)'
        }
        stage('Deploy') {
            sh './jenkins/scripts/deliver.sh'
            sleep(60)
            sh './jenkins/scripts/kill.sh'
        }
    }
}