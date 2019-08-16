# docker-terragrunt

Run with a command like this:
`docker run -it --rm --mount type=bind,source="$(pwd)",target="/work"  -e AWS_ACCESS_KEY_ID="$(aws configure get aws_access_key_id)" -e AWS_SECRET_ACCESS_KEY="$(aws configure get aws_secret_access_key)" -e AWS_SESSION_TOKEN="$(aws configure get aws_session_token)" -e AWS_DEFAULT_REGION="us-east-1" lordmuffin/terragrunt`