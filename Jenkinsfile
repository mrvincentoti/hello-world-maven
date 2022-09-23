node{
    stage('Checkout'){
        git 'https://github.com/mrvincentoti/hello-world-maven.git'
    }
    stage('Compile Package'){
        sh 'mvn clean package'
    }
}