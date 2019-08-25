pipeline {

	agent none

	

	environment {
	    MyKeyID="myCustomValue1"
	}
	
	stages {

	stage('Descargar codigo fuente') {
		environment{
		    MyKeyID="MyCustomValue"
		}
    	steps {
    		script {
          		node {
                      parallel("first": {
                        echo "hello"
                        },
                        "second": {
                            echo "world"
                        }
                     )
                     
                println "\n Mi primer stage.\n MyKeyID value es: ${MyKeyID}\n"
                      
        				
          		}
        	}
    	}
	}
	stage('Descargar codigo fuente practico') {

    	steps {
    		script {
          		node {
                      parallel("first": {
                        echo "hello"
                        },
                        "second": {
                            echo "world"
                        }
                        )
                        
        				writeFile file: 'comments.txt', text: 'test hello world, saving this text.'
        				archiveArtifacts artifacts: 'comments.txt'
        				build job: 'comparte/nuevo_lunes', parameters: [[$class: 'StringParameterValue', name: 'MyCustomParameter', value: 'Whatever']], propagate: true, wait: true
                        println "\n Mi Segundo stage.\n"  
                    
						
          		}
        	}
    	}
	}
    }

}

