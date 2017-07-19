node('cloud-d15') {
    def root = tool name: 'Go1.8', type: 'go'
    env.GOROOT = root
    env.GOPATH = "/home/jenkins/go"
    sh "echo ${GOPATH} && echo ${GOROOT} && mkdir -p ${GOPATH}"
    env.PATH = "${root}/bin:${env.GOPATH}/bin:${env.PATH}"

            stage 'Checkout'
        
            git url: 'https://github.com/jmvanryn/golang-ci-jenkins-pipeline.git'
        
            stage 'preTest'
            sh 'go version '
            sh 'go get -u github.com/tools/godep && echo ${GOPATH}'
            sh 'godep restore'
            
            stage 'Test'
            sh 'go vet'
            sh 'go test -cover'
            
            stage 'Build'
            sh 'go build .'
            
            stage 'Deploy'
            // Do nothing.
}
