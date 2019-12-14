node {

stage ('scm checkout') {
git url: 'https://github.com/yogeshgund/maven-project.git', branch: 'master'
}

	parallel createpackage: {
	stage('maven package goal') {
sh 'mvn package'
}
	}, installm2mavenrepo: {

  stage('install maven goal')

{ sh 'mvn install'
}
  },
  failFast: true
}

