node() {
    docker.withRegistry('http://my-docker-reg', 'my-docker-reg-creds') {
    
        git url: "https://github.com/abid-khairul/game-of-life", credentialsId: ''
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "your-project-name"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
