pipeline {
  agent none
  stages {
    stage('Prepare test environment') {
      parallel {
        stage('Build env Win') {
          steps {
            build 'VM_controller'
            catchError() {
              build 'win_installer'
            }

          }
        }
        stage('build env lxc') {
          steps {
            build 'LXC_controller'
            build 'alio_builder'
            catchError() {
              build 'alio_builder'
            }

          }
        }
      }
    }
    stage('Testing: cfwipc') {
      steps {
        build 'cfwipc_test'
      }
    }
    stage('Testing: cfwstorage') {
      steps {
        build 'cfwstorage_tests'
      }
    }
    stage('Testing: cfwlog') {
      steps {
        build 'cfwstorage_tests'
      }
    }
    stage('Testing: cfwnetwork') {
      steps {
        build 'cfwnetwork_test'
      }
    }
    stage(' Testing: cfwretail') {
      steps {
        build 'cfwnetwork_tests'
      }
    }
    stage('Testing: Win installer') {
      steps {
        build 'Win_installer_tests'
      }
    }
  }
}