node('cloud-d15') {
    def root = tool name: 'Go1.8', type: 'go'
    ws {
        withEnv(["GOROOT=${root}", "PATH+GO=${root}/bin"]) {
            sh 'export GOPATH=$(go env GOPATH) && mkdir -p ${GOPATH} '
            sh 'export PATH=${GOPATH}/bin:$PATH'
            
            stage 'Checkout'
        
            git url: 'https://github.com/grugrut/golang-ci-jenkins-pipeline.git'
        
            stage 'preTest'
            sh 'go version '
            sh 'go get -u github.com/tools/godep'
            sh 'godep restore'
            
            stage 'Test'
            sh 'go vet'
            sh 'go test -cover'
            
            stage 'Build'
            sh 'go build .'
            
            stage 'Deploy'
            // Do nothing.
        }
    }
}
