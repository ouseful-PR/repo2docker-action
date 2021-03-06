
# <a href="https://github.com/jupyter/repo2docker"><img src="https://raw.githubusercontent.com/jupyter/repo2docker/3fa7444fca6ae2b51e590cbc9d83baf92738ca2a/docs/source/_static/images/repo2docker.png" height="40px" /></a>  repo2docker GitHub Action


Trigger [repo2docker](https://github.com/jupyter/repo2docker) to turn your GitHub repository into a Jupyter enabled docker image.  This will automatically attempt to build an environment from configuration files found in your repository in the [manner described here](https://repo2docker.readthedocs.io/en/latest/usage.html#where-to-put-configuration-files).

Read the full docs on repo2docker for more information:  https://repo2docker.readthedocs.io

**The only docker registry supported at the moment is Dockerhub.**

## Recommended Usage

You must copy the contents of your repository to use this action as illustrated below:

```yaml
name: Build Notebook Container
on: [push] # You may want to trigger this Action on other things than a push.
jobs:
  build:
    runs-on: ubuntu-latest
    steps:

    - name: checkout files in repo
      uses: actions/checkout@master

    - name: try-local-build
      uses: machine-learning-apps/repo2docker-action@master
      with:
        DOCKER_USERNAME: ${{ secrets.DOCKER_USERNAME }}
        DOCKER_PASSWORD: ${{ secrets.DOCKER_PASSWORD }}
        IMAGE_NAME: "your_username/your_image_name"
```


## Mandatory Inputs

- `DOCKER_USERNAME`:
    description: Docker registry username 
- `DOCKER_PASSWORD`:
    description: Docker registry password
- `IMAGE_NAME`:
    description: name of the image.  Example - myContainer

## Outputs

- `IMAGE_SHA_NAME`:
    description: The name of the docker image, which is tagged with the SHA.
- `IMAGE_URI`
    description: The URI on DockerHub that corresponds to the image.
