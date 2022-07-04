# Installation

## Get Docker artifacts

Get the compose file

```bash
curl -O https://s3.us-east-2.amazonaws.com/mycompany/docker-compose.yml
```

## Configure environment variables

You need to set the following environment variables to configure your product properly:

Environment variables creation is performed by the snippet below:

```bash
export AWS_ACCESS_KEY_ID=<your access key id>
export AWS_SECRET_ACCESS_KEY=<your secret access key>
export AWS_DEFAULT_REGION=us-east-2
```

After that, log in using the AWS CLI dedicated command:
