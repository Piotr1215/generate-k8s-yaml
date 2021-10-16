# How to create and validate Kubernetes YAML - playground

This project includes a devcontainer setup with following tools installed (latest versions):

- <s>kubernetes</s>
- <s>kubectl</s>
- <s>helm</s>
- docker-from-docker
- docker-compose
- yq
- cdk8s
- naml
- <s>Go</s>
- TypeScript
- vs code extensions
- kubeval

Please note that the image is relatively big (>1.5 GB) given all the tools installed. Some of the tools/features are disabled in the .devcontainer file:
- kubernetes
- kubectl
- helm

You can easily enable them by editing [features section](.devcontainer/devcontainer.json#L35) in the devcontianer file, uncomment features you like to enable and run: <p><kbd>Remote-Containers: Rebuild and Reopen in Container</kbd></p>

 ## A note on devcontianer setup.

 Here we are taking advantage of a new preview feature; [**dev container features**](https://code.visualstudio.com/docs/remote/containers#_dev-container-features-preview). This functionality is making it easier to install and configure devcontainer by adding a thin abstraction layer. Instead of adding potentially complicated commands directly to a Dockerfile, you can just enable/disable a feature directly in a devcontainer file. [List of features](https://github.com/microsoft/vscode-dev-containers/tree/main/script-library/docs) is growing, so keep an eye on it if the feature you want is currenly missing. You will notice that docker CLI has access to the contianers and images on your host. Please note that the CLI in this contianer runs as root. To learn more about this feature, check out [this repo](https://github.com/microsoft/vscode-dev-containers/tree/main/containers/docker-from-docker)

## How to use the playground

With the tools pre-installed you can experiment with different ways to generate Kubernetes YAML. Each folder contians a code sample as well as README file to test the tools.
