pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                script {
                    writeFile(file: 'base64File', text: 'jenkins book', encoding = 'UTF-8')
                    def content = readFile(file: 'base64File', encoding = 'UTF-8')
                    echo "${content}"
                }
            }
            post {
                always {
                    echo 'stage post always'
                }
            }
        }
    }
    post {
        changed {
            echo 'pipeline post changed'
        }
        always {
            echo 'pipeline post always'
        }
        success {
            echo 'pipeline post success'
        }
    }
    options {
        // 防止构建占用空间，这里设置为10来保持10个构建
        buildDiscarder(logRotator(numToKeepStr: '10'))
        // 拉取源码的位置，默认为工作空间的根目录
        checkoutToSubdirectory('subdir')
        // 禁止构建的时候运行多次pipeline
        disableConcurrentBuilds()
        // 重试次数
        retry(3)
        // 超时时间，超过则自动关闭流水线，默认单位为小时
        timeout(time: 15, unit: 'MINUTES')
    }
}