---
title: "Install CLI Tools"
chapter: false
weight: 22
---

The [AWS Command Line Interface](https://aws.amazon.com/cli/) (CLI) is already installed in Cloud9.

For this workshop, we are also going to use the [Amazon ECS CLI](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_CLI_installation.html). The ECS CLI supports the [Docker Compose](https://docs.docker.com/compose/overview/) file format and has similar commands, to simplify the deployment of multi-container Docker applications.

{{% notice tip %}}
In this workshop we will give you the commands to download the Linux
binaries. If you are running macOS / Windows, please [see the official docs
for the download links.](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_CLI_installation.html)
{{% /notice %}}

#### Download and install the latest ECS CLI release
```
sudo curl -o /usr/local/bin/ecs-cli https://amazon-ecs-cli.s3.amazonaws.com/ecs-cli-linux-amd64-latest

sudo chmod ugo+x /usr/local/bin/ecs-cli
```

#### Verify the download (optional)
```
echo "$(curl -s https://amazon-ecs-cli.s3.amazonaws.com/ecs-cli-linux-amd64-latest.md5) /usr/local/bin/ecs-cli" | md5sum -c -
```

#### Verify the binary
```
ecs-cli --version
```

Your output should resemble:

![verify](/images/prerequisites/ecs_cli_verify.png)

#### Install CLI utilities
```
sudo yum -y install jq
```

#### Configure the AWS region

```
aws configure set default.region $(curl -s 169.254.169.254/latest/dynamic/instance-identity/document | jq -r .region)
```

