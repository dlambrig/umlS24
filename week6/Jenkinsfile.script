podTemplate(containers: [
  containerTemplate(
    name: 'gradle',
    image: 'gradle:6.3-jdk14',
    command: 'sleep',
    args: '30d'
    ),
  ]) {
    node(POD_LABEL) {
      stage('Run pipeline against a gradle project - test MAIN') {
	container('gradle') {
          stage('Build a gradle project') {
            echo "I am the ${env.BRANCH_NAME} branch"
          }
          stage('Code coverage') {
	    sh 'printenv'
            echo "My CC branch is: ${env.CHANGE_BRANCH}"
            if (env.BRANCH_NAME == "feature") {
              echo "I am the ${env.BRANCH_NAME} branch"
            }
          }
        }
      }   
    }
}
