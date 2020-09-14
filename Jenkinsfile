 
node('DOTNETCORE'){
	stage('SCM'){
		checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/ma7ammad/eShopOnWeb']]])
	}
	stage('Build'){
		try{
    echo '"$WORKSPACE/eShopOnWeb/src/ApplicationCore"'
		sh 'dotnet build "$WORKSPACE/eShopOnWeb/src/ApplicationCore"'
		}finally{
		archiveArtifacts artifacts: "$WORKSPACE/eShopOnWeb/src/ApplicationCore/*.*"
		}
	}
	stage('Test'){
		echo 'Execute unit tests'
	}
	stage('Package'){
		echo 'Zip it up'
	}
	stage('Deploy'){
		echo 'Push to deployment'
	}
	stage('Archive'){
		//archiveArtifacts artifacts: '"$WORKSPACE/eShopOnWeb/src/ApplicationCore/*.*"
	}
}
