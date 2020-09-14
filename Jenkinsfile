node('DOTNETCORE'){
	stage('SCM'){
		checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/ma7ammad/eShopOnWeb']]])
	}
	stage('Build'){
		try{
    echo '"$WORKSPACE/src/ApplicationCore"'
		sh 'dotnet build "$WORKSPACE/src"'
		}finally{
		archiveArtifacts artifacts: "src/ApplicationCore/*.*"
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
		//archiveArtifacts artifacts: '"$WORKSPACE/src/ApplicationCore/*.*"
	}
}
