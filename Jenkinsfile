pipeline {
  agent {
    kubernetes {
      yaml """\
        apiVersion: v1
        kind: Pod
        metadata:
          labels:
            some-label: some-label-value
        spec:
          containers:
          - name: alpine
            image: alpine
            command:
            - cat
            tty: true
        """.stripIndent()
    }
  }
  stages {
    stage('setup') {
      steps {
        container('alpine') {
          sh 'apk add cmake build-base boost-dev libogg-dev flac-dev libvorbis-dev git-lfs'
        }
      }
    }
    stage('build') {
      steps {
        container('alpine') {
          sh 'cmake -B build'
          sh 'cmake --build build'
        }
      }
    }
    stage('test') {
      steps {
        container('alpine') {
          sh 'cmake -DNIMEDIA_TESTS=ON'
          sh 'git lfs pull -X ""'
          sh 'cmake --build build --target test'
        }
      }
    }
  }
}
