pipeline {
agent any 
stages {
stage('inital') {

    steps {
        script{
            switch(env.UI){

                case 'Test':
                env.UI = "10.128.15.206"
                break
                
                case 'UAT':
                env.UI = "10.128.15.206"

                case 'Prod':
                env.UI = "10.128.15.206"
            

            }
            switch (env.API) {
               case 'Test':
                env.API = "10.128.15.209"
                break
                
                case 'UAT':
                env.API = "10.128.15.209"

                case 'Prod':
                env.API = "10.128.15.209" 
            }
        }
    }
}
stage('common') {
    steps {

       sh '''
        echo 'this is common'
        
        '''
    }
}
stage('deploy') {
    when{
         
            expression {params.deploy == 'API' || params.deploy == 'UI'}
        
    }

    steps{
        sh '''
        echo 'this is UI or API'
        '''
    }
}

stage ('UI'){
    
  when {
		expression {
		environment name: 'env', value: 'Test' 
		}

    }
    steps{
    
        sh '''
        echo "this is Test"
        '''
    }

}
stage ('API+ uat') {
    when {
		expression {
		environment name: 'env', value: 'Uat' 
		}

    }
    steps{
    
        sh '''
        echo "this is Uat"
        '''
    }
}

stage('API+Test'){
    when {
		expression {
		environment name: 'env', value: 'Test' 
		}
    }

        steps{
           sh '''
        echo "this is api+test"
        ''' 
        }

}

stage('API+Prod') {
    when {
        expression {
            environment name: 'env', value: 'Prod' 
        }
    }

    steps{
        sh'''
        echo 'this is API+Prod'
        '''
    }
}
}

}
