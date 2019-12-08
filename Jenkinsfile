pipeline {
agent any
stages
{
stage ('cloning code')
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
    sh'mvn compile' }}}
stage ('test my project')
{
steps
{
withMaven(jdk: 'LocalJDK', maven: 'LocalMaven') {
    sh'mvn test' }}}
stage ('package my code')
{
steps
{
withMaven(jdk: 'LocalJDK', maven: 'LocalMaven') {
    sh'mvn package' }}}
stage ('install my code')
{
steps
{
withMaven(jdk: 'LocalJDK', maven: 'LocalMaven') {
    sh'mvn install' }}}
stage ('verify my code')
{
steps
{
withMaven(jdk: 'LocalJDK', maven: 'LocalMaven') {
    sh'mvn verify' }}}
stage ('deploy my code')
{
steps
{
  sshagent (credentials: ['deploy-dev']) {
    sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@http://172.31.39.233:/var/lib/tomcat/webapps'
  }}}
}
}
