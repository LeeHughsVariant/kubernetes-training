# Kubectl - The Kubernetes Command-Line Tool

## Goals

1. Install kubectl
2. Configure your kubeconfig
3. Inspect your Kubernetes resources with kubectl
4. Create Kubernetes resources with kubectl
5. Delete Kubernetes resources with kubectl

## Install kubectl

Try running the following command to see if you already have kubectl installed:
```bash
kubectl version --client
```

If you do not have kubectl installed, follow the steps below to install it.

https://kubernetes.io/docs/tasks/tools/

Windows:
```powershell
curl -LO "https://dl.k8s.io/release/v1.24.0/bin/windows/amd64/kubectl.exe"
```
Then add kubectl.exe to your PATH

Mac (Intel):
```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/darwin/amd64/kubectl"
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl
sudo chown root: /usr/local/bin/kubectl
```

Mac (Silicone):
```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/darwin/arm64/kubectl"
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl
sudo chown root: /usr/local/bin/kubectl
```

## Configure your kubeconfig file

kubectl allows you to manage configuration with multiple cluters via your kubeconfig file.

As a prerequisite to this section, you must have aws SSO configured via the AWS CLI tool.

https://drivevariant.atlassian.net/wiki/spaces/CLOUD/pages/1384513619/Getting+Credentials+using+AWS+Single+Sign-On+SSO

Once you have SSO set up with the AWS CLI, you must update your [kubeconfig](https://kubernetes.io/docs/concepts/configuration/organize-cluster-access-kubeconfig/) which can be done automatically with the AWS CLI.

The syntax for the command is
`aws eks update-kubeconfig --name <cluster-name> --region <cluster-region> --profile <profile>`

The "profile" depends on the profile name set while configuring SSO.

The "cluster-name" and "cluster-region" are as follows:

| Environment            | Cluster Name     | Cluster Region | AWS Account      |
|------------------------|------------------|----------------|------------------|
| Variant Development    | variant-dev      | us-east-1      | Variant-Dev      |
| Variant QA             | qa-one           | us-east-1      | Variant-QA       |
| Variant Staging        | variant-stage    | us-east-1      | Variant-Stage    |
| Variant Production     | variant-prod     | us-east-1      | Variant-Prod     |
| Enterprise Development | enterprise-dev   | us-east-1      | Enterprise-Dev   |
| Enterprise Staging     | enterprise-stage | us-east-1      | Enterprise-Stage |
| Enterprise Production  | enterprise-prod  | us-east-1      | Enterprise-Prod  |
| USXpress Development   | usxpress-dev     | us-east-2      | USX-AWS-DEV      |
| USXpress QA            | qa-one           | us-east-2      | USX-AWS-QA       |
| USXpress Staging       | usxpress-stage   | us-east-2      | USX-AWS-Staging  |
| USXpress Production    | usxpress-prod    | us-east-2      | USX-AWS-Prod     |


### kube contexts
Once you have configured your kubeconfig try running the following command to view what clusters you have configured access to.

`kubectl config get-contexts`

This will also show you what context is currently active. To switch kube-contexts run the following command:

`kubectl config use-context {context-name}`
