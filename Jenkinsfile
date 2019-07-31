//Stage nested with input  Procced or Abort with library to catch the exception abort
import org.jenkinsci.plugins.workflow.steps.FlowInterruptedException
pipeline {

	agent none
	environment {
	    MyKeyID="myCustomValue1"
	}
	
	stages {
	
stage("stage master") {
		steps {
    			script {
					
					stage("inner stage 1") {
						script {
						
                            //each node can be a virtual machine
							node {
								println "inner stage"
							}

							
						}
					}

					stage("inner stage 2") {
						script {
						
							node {
								println "inner stage"
							}

							
						}
					}
            }
        }
    }

	stage('Descargar codigo fuente') {
	    environment {
    	    MyKeyID="myCustomValue2x"
    	}
    	steps {
    		script {
          		node {
        				println "\n Mi primer stage.\n MyKeyID value es: ${MyKeyID}\n"
          		}
        	}
    	}
	} 
	
	stage('Test') {
    	steps {
    		script {
          		node {
        			println "Mi segundo stage esta en ejecucion. KeyID: $MyKeyID"
          		}
        	}
    	}
	}

    stage('Input Test') {
    steps {
        script {
            try {
                timeout(time: 30, unit:"SECONDS") {
                    input(message: "Are you sure for deploy?")
                }                    
            }
            catch(FlowInterruptedException error) {
                def user = error.getCauses()[0].getUser().toString()
                //SYSTEMS means timeout
                if ('SYSTEM' == user) {
                    println "Ejecucion del pipeline abortado automaticamente por el sistema. ${user}"
                }
                //if user is distinct from SYSTEM, then a jenkins user aborted the pipeline dploy manually
                else {
                    println "Ejecucion del pipeline abortado por el usuario ${user}"
                }
            }
            finally {
                node {
                    println "Init deploy to production"
                }
            }
        }
    }
}
	
	stage('Fin') {
    	steps {
    		script {
          		node {
        			println "Mi segundo stage esta en ejecucion. KeyID: $MyKeyID"
          		}
        	}
    	}
	}
	    
}

}