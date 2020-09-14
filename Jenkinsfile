node('DOTNETCORE'){
	stage('SCM'){
		checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/ma7ammad/eShopOnWeb']]])
	}
	stage('Build'){
		try{
    echo '"$WORKSPACE/src/ApplicationCore"'
		sh 'dotnet build "$WORKSPACE/src/ApplicationCore"'
		sh 'dotnet build "$WORKSPACE/src/BlazorAdmin"'
		sh 'dotnet build "$WORKSPACE/src/BlazorShared"'
		sh 'dotnet build "$WORKSPACE/src/Infrastructure"'
		sh 'dotnet build "$WORKSPACE/src/PublicApi"'
		sh 'dotnet build "$WORKSPACE/src/Web"'
		sh 'dotnet build "$WORKSPACE/tests/UnitTests"'
		sh 'dotnet build "$WORKSPACE/tests/IntegrationTests"'
		}finally{
		archiveArtifacts artifacts: "src/ApplicationCore/*.*"
		}
	}
	stage('Test'){
		sh 'dotnet test "$WORKSPACE/tests/UnitTests"'
		sh 'dotnet test "$WORKSPACE/tests/IntegrationTests"'
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
