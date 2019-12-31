# Introduction

Azure agent is used to run build & release pipeline of Azure DevOps.

# Quick reference

https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/docker?view=azure-devops

# How to build the image

You can use the docker image from my docker hub https://hub.docker.com/r/mikejianzhang/azure-agent directly  

You can also buld the image by yourself using below command:

```sh
./build.sh azure-agent:<tag>
```

> If you are behind company firewall, set environment variables "http_proxy", "https_proxy" and "no_proxy" accordingly before running the build.


# How to use this image

## Run as backend daemon

```sh
$ docker run -it -d --name some-agent \
        -e AZP_URL=your-azure-devops-url \
        -e AZP_TOKEN=your-azure-devops-api-token \
        -e AZP_AGENT_NAME=some-agent \
        -e AZP_POOL=your-azure-devops-agent-pool \
        -e AZP_AGENTPACKAGE_URL=the-zure-devops-agent-package \
        azure-agent:<tag> 
```

### Environment variables


Name | Required | Comment 
---|---|---
AZP_URL | Yes | The Azure DevOps server url. i.e. https://<host>/tfs
AZP_TOKEN | Yes | API token with enough permission used to connect to Azure DevOps server
AZP_AGENT_NAME | yes | Agent name shown in agent pool
AZP_POOL | yes | Agent pool name
AZP_AGENTPACKAGE_URL | No | You can specify the download url of azure agent package to overwrite the default url
