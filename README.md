pipeline {
    agent any
    
    stages {
        stage ('compile') {
           
           steps {
                withMaven(maven : 'maven_3_8_1')
                    sh 'mvn clean compile'
                }
            }
        }
    
        stages {
           stage ('testing') {
           
              steps {
                withMaven(maven : 'maven_3_8_1')
                    sh 'mvn test'
                }
            }
        }
    
        stages {
           stage ('deployment') {
           
              steps {
                withMaven(maven : 'maven_3_8_1')
                    sh 'mvn deploy'
                }
            }
        }
    }
