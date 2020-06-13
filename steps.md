# Steps

- Clone https://github.com/awslabs/ecs-refarch-continuous-deployment - This has the cloud formation stack  
- Install AWS CLI
- Create AWS account and Configure CLI
    - Created IAM user
    - Update credentials in AWS CLI
        - Configure AWS
            ```
                aws configure
            ```
        - Create Stack
            ```
                aws cloudformation create-stack --stack-name testpipeline --capabilities CAPABILITY_IAM CAPABILITY_NAMED_IAM CAPABILITY_AUTO_EXPAND --template-body **PATH** --parameters ParameterKey=GitHubUser,ParameterValue=**GitHubUser** ParameterKey=GitHubToken,ParameterValue=**GitHubToken**
            ```
        - aws cloudformation list-stacks
        - aws cloudformation delete-stack --stack-name testpipeline
        - aws cloudformation describe-stacks
        - aws s3api get-bucket-tagging --bucket **BUCKET_NAME**
        - Update  stack
            ```
            aws cloudformation create-change-set --stack-name myteststack --change-set-name SampleChangeSet --template-body **PATH** --parameters ParameterKey=TagName,ParameterValue=whateveriwanttodo
            ```
        - Describe change set
            ```
            aws cloudformation describe-change-set --change-set-name SampleChangeSet --stack-name myteststack
            ```
        - Execute changeset
            ```
            aws cloudformation execute-change-set --change-set-name SampleChangeSet --stack-name myteststack
            ```
        - Create Change Set
            ```
            aws cloudformation create-change-set --change-set-name UpdatedGitParameter --stack-name testpipeline --capabilities CAPABILITY_IAM CAPABILITY_NAMED_IAM CAPABILITY_AUTO_EXPAND --template-body file://///**PATH** --parameters ParameterKey=GitHubUser,ParameterValue=**GitHubUser** ParameterKey=GitHubToken,ParameterValue=**GitHubToken**
            ```
        - Describe Change Set
            ```
            aws cloudformation describe-change-set --change-set-name UpdatedGitParameter --stack-name testpipeline
            ```
        - Execute Change Set
            ```
            aws cloudformation execute-change-set --change-set-name UpdatedGitParameter --stack-name testpipeline
            ```
