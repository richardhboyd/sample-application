# sam-app

STACKNAME=GH-Roles

aws cloudformation deploy \
  --template-file ./templates/infrastructure.yaml \
  --stack-name $STACKNAME \
  --parameter-overrides GitHubOrg=richardhboyd RepositoryName=sample-application OIDCProviderArn=""\
  --capabilities CAPABILITY_IAM \
  --region us-west-2

aws cloudformation describe-stacks --stack-name GH-Roles --output text --query "Stacks[?StackName=='$STACKNAME'][].Outputs[?OutputKey=='Role'].OutputValue"