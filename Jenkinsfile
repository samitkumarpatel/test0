def choiceArray = []
node {
    
    checkout scm

    // representation of checkout scm
   /*
    sh """
        mkdir -p src src/$BUILD_NUMBER
    """
   */
    def folders = sh(returnStdout: true, script: "ls src")
    
    folders.split().each {
        choiceArray << it
    }
    /*
    print choiceArray
    print choiceArray.size()
    properties([
        parameters([
            choice(name: 'folder', choices: choiceArray )
        ])
    ]) 
    */
}

pipeline {
    agent any;
    parameters { choice(name: 'CHOICES', choices: choiceArray, description: 'Please Select One') }
    stages {
        stage('debug') {
            steps {
                echo "Selected choice is : ${params.CHOICES}"
            }
        }
    }
}
