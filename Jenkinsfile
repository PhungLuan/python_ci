pipeline {
  agent any
  triggers { pollSCM('*/1 * * * *') }
  stages {
    stage('test') {
      steps {
        sh '''PYTHONPATH=\'\'
nosetests --with-xunit --all-modules --traverse-namespace --with-coverage --cover-package=project1 --cover-inclusive
python -m coverage xml --include=project1*
pylint -f parseable -d I0011,R0801 project1 | tee pylint.out'''
      }
    }
  }
}
