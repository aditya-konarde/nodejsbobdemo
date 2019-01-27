@Library('github.com/fabric8io/osio-pipeline@master') _

osio {

  config runtime: 'node'

  ci {

    def resources = processTemplate(params: [
          release_version: "1.0.${env.BUILD_NUMBER}"
    ])

    build resources: resources

  }

  cd {

    stage("Other OpenShift Cluster") {
        openshift.withCluster('oc login https://api.starter-us-east-2.openshift.com', '2-0LH6vHl_YFjrnJaDVpmTWQ3vSZ_XDu3Un1R-RqNg4' ) {
            openshift.withProject( 'hshinde-jenkins' ) {
                openshift.selector( 'deploymentconfig/jenkins' ).describe()
            }
        }
    }

  }
}
