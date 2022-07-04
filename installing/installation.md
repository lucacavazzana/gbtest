# Installation

## Get Docker artifacts

Myproduct is deployed as a set of containerized services running on Docker and managed via Docker Compose. Since you have access to the public internet you can get the latest version of the myproduct Docker Compose file with the specs of all the images required by Docker. We suggest creating a folder named myproduct in the home directory of your user, then simply run the following command to get the most updated file:

```bash
mkdir myproduct; cd myproduct
curl -O https://s3.us-east-2.amazonaws.com/myproduct/compose/$(curl https://s3.us-east-2.amazonaws.com/myproduct/compose/stable.txt)/docker-compose.yml
```

## Configure environment variables

You need to set the following environment variables to configure Myproduct properly:

**MYPRODUCT\_CUSTOMER**: the customer name. The name has to match the one linked to the myproduct license.

**MYPRODUCT\_BASE\_URL**: it is the endpoint of the myproduct APIs that will be used to interact with the CLI. Since you are installing myproduct as an all-in-one instance you can set it to localhost port 8000.

{% hint style="warning" %}
You’d better save all exported variables in your `~/.bashrc` file for convenience
{% endhint %}

Environment variables creation is performed by the snippet below:

```bash
export MYPRODUCT_CUSTOMER=<your name or your organization name>
export MYPRODUCT_BASE_URL=http://<myproduct server dns address>:8000
```

In order to login into AWS ECR and pull the updated myproduct containers images you also need to set the AWS authentication variables accordingly to the values shared by your Professional Services contact person. To set the variables run the following command:

```bash
export AWS_ACCESS_KEY_ID=<your access key id>
export AWS_SECRET_ACCESS_KEY=<your secret access key>
export AWS_DEFAULT_REGION=us-east-2
```

After that, log in using the AWS CLI dedicated command:

```bash
aws ecr get-login-password --region us-east-2 | docker login -u AWS --password-stdin https://48579051247.dkr.ecr.us-east-2.amazonaws.com
```
