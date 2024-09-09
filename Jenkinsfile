pipeline {
    agent any
    
    environment {
        BUILD_FILE_NAME = 'home.txt'
    }

    stages {
        stage('build') {
            steps {
                cleanWs()
                echo 'Hello World'
                echo "$BUILD_FILE_NAME"
                sh '''mkdir -p build
                    \\touch build/home.txt
                    echo kitchen >> $BUILD_FILE_NAME
                    cat build/home.txt
                    echo livingroom >> $BUILD_FILE_NAME
                    echo $BUILD_FILE_NAME
                    '''
            }
        }
        stage('test') {
            steps {
                sh '''test -f $BUILD_FILE_NAME
                grep kitchen $BUILD_FILE_NAME
                grep livingroom $BUILD_FILE_NAME'''
            }
        }
    }
}
