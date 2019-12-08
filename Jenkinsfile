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
stage ('deploy to tomcat')
{
steps
{
  sshagent(['tomcat2']) {
    sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@54.90.188.161:/var/lib/tomcat/webapps'
  }}}
}
}
