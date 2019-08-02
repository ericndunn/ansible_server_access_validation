pipeline {
    agent { label 'MASTER' }
        parameters {
        string(defaultValue: 'YOUR_USER_ID', description: 'Artifictory User ID', name: 'MY_USERID')    
        choice(choices: ['inventory', 'null'], 
                          description: 'Name of Inventory File', 
                          name: 'INV_FILE')
        choice(choices: ['all', 
                         'PROD', 
                         'SIT', 
                         'PERF',
                         'UAT',
                         'DEV'], 
                         description: 'Inventory Groups', 
                         name: 'INV_GRP')
    }
    stages {
        stage('Run Ansible Access operation'){
        
            steps {

            wrap([$class: 'AnsiColorBuildWrapper', colorMapName: "xterm"]) {
                    echo 'Validate Access'
                    //sh 'ansible-playbook -i dev-servers site.yml'
                    ansiblePlaybook credentialsId: 'AG19884_PK',
                    installation: 'ansible', 
                    inventory: '/Users/${MY_USERID}/${INV_FILE}',
                    limit: '${INV_GRP}',
                    playbook: '${WORKSPACE}/server_access_status.yml',
                    colorized: true
                }
            }
        }

        stage('Demo Performance'){
            steps {
                echo 'Clap if you liked the demo!'
            }
        }

    }
}
