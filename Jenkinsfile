pipeline {
agent any
stages
{
steps
{git 'https://github.com/yogeshgund/maven-project.git'
}
}
stage ('compile my project')
{
steps
{
withMaven(jdk: 'LocalJDK', maven: 'LocalMaven') {
    sh'mvn compile'
}
}
}
