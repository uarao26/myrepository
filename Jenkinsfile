node('node'){
    stage 'Checkout'
         checkout scm
    stage 'Test'
        env.NODE_ENV = "test"
        print "Environment will be : ${env.NODE_ENV}"
        sh 'node -v'
        sh 'npm install'
        sh 'npm test'
    stage 'Build Docker'
        sh './dockerBuild.sh'
    stage 'Deploy'
         echo 'Push to Repo'
         sh './dockerPushToRepo.sh'
    stage 'Cleanup'
         sh 'rm node_modules -rf'
         mail body: 'project build successful',
                     from: 'uarao26@gmail.com',
                     replyTo: 'uarao26@gmail.com',
                     subject: 'project build successful',
             }
}
