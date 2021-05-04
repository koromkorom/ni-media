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
          sh 'apk add cmake'
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
  }
}
