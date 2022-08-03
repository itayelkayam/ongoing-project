timestamps {

node () {
    stage ('Workspace Cleanup') {
	    cleanWs()
	}
	stage ('My-Python-App - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '', url: 'https://github.com/itayelkayam/ongoing-project.git']]]) 
	}
	stage ('My-Python-App - Build') {
 	
sh """ 
ls
echo "hello world"
cd flaskexample/
docker build -t itayelkayam/$IMAGENAME:v1.0 . 
 """		// Shell build step
sh """ 
export KEYID=$KEYID SECRETKEY=$SECRETKEY REGION=$REGION
 """		// Shell build step
sh """ 
aws configure set aws_access_key_id $KEYID
aws configure set aws_secret_access_key $SECRETKEY
aws configure set region $REGION
aws configure set output json 
 """		// Shell build step
sh """ 
aws ecr get-login-password --region $REGION | docker login --username AWS --password-stdin 259826285692.dkr.ecr.eu-central-1.amazonaws.com
docker tag itayelkayam/$IMAGENAME:v1.0 259826285692.dkr.ecr.eu-central-1.amazonaws.com/ongoing-project-itay:$TRY
docker push 259826285692.dkr.ecr.eu-central-1.amazonaws.com/ongoing-project-itay:$TRY 
 """ 
	}
}
}
