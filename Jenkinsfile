pipeline{
    agent {
      label 'CD-Agent'
    }
    parameters{
       booleanParam(name: "LoadJenkinsfile", defaultValue: false, description: 'Only Check in case jenkinsfile is updated in git repo.')
       choice choices: ['dbxp-releases'], description: 'specify the path to copy artifacts from release in Jfrog', name: 'DBXP_TARGET_REPO'
       choice choices: ['dfs-common-releases'], description: 'specify the path to copy artifacts from release in Jfrog', name: 'COMMON_TARGET_REPO'
       string defaultValue: 'dbxp.2.1.0', description: 'Specify the release tag', name: 'RELEASE_TAG', trim: false
       string defaultValue: '/home/mobiquity/dbxp.2.1.0', description: 'Provide path to create bundle', name: 'Installer_Path', trim: false
       string defaultValue: 'common-installer', description: 'Provide name for bundle', name: 'Installer_Folder', trim: false
       string defaultValue: 'X.01.00', description: 'Specify the release version', name: 'releaseVersion', trim: false
       booleanParam defaultValue: false, description: 'Check this box to add logging service in the bundle', name: 'LOGGING_SERVICE_ENABLED'
       booleanParam defaultValue: false, description: 'Check this box to add reporting in the bundle', name: 'REPORTING_ENABLED'
       booleanParam defaultValue: false, description: 'Check this box to add MAAS in the bundle', name: 'MAAS_ENABLED'
    }
        stages {
            stage('Update Config'){
                when { expression {params.LoadJenkinsfile}}
                steps{
                    echo 'Latest Jenkinsfile Loaded Successfully'
                    sh 'exit 0'
                }
            }   
         
        stage('Common: Copy Artifacts and Git Tagging') {
            when { expression { !params.LoadJenkinsfile }
             expression { env.TAGGING == "true" }
            }
            steps {
                echo 'Copy Artifacts and Git Tagging'
            }
        }
            
         
        stage('DBXP: Copy Artifacts and Git Tagging') {
            steps {
                echo 'Copy Artifacts and Git Tagging'
            }
        }
        
            
        stage('Dependent Repos: Git Tagging') {
            steps {
                echo 'Copy Artifacts and Git Tagging'
            }
        }
    }
}
