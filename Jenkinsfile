node {

def mvnHome

stage('Prepare') {

git url: 'https://github.com/bg1854/devops-infrastructure', branch: 'develop'

mvnHome = tool 'mvn'

}

stage('Build') {

if (isUnix()) {

sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"

} else {

bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)

}

}

stage('Unit Test') {

junit '**/target/surefire-reports/TEST-*.xml'

archive 'target/*.jar'

}

stage('Integration Test') {

if (isUnix()) {

sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean verify"

} else {

bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean verify/)

}

}
}












