# Concourse CI Starter

This repository holds a collection of example pipelines for a quick start with Concourse CI (http://concourse.ci).

## Instructions

For this setup Docker and Docker-Compose is required. Make sure you have these installed.
Then edit the `docker-compose.yml` within the `docker-compose` directory and set username, password and ip accordingly.
Finally run `docker-compose up` within this directory.

Your Concourse CI test instance should be available at http://127.0.0.1:8080

## Create Pipelines
Download the fly-cli and use a shell to execute the following commands:

```
fly -t ci-starter -c http://127.0.0.1:8080
fly -t ci-starter login
```

This will connect your fly-cli with your concourse-ci instance. The `-t` flag denotes the target.
You can connect multiple instances to your fly-cli.

Next, you need to create a `config.yml` from the ``config.template.yml` file in the root folder. 

Assuming you are in the root folder of this repository, you have to execute following commands to setup the pipelines

```
fly -t ci-starter set-pipeline --pipeline full_pipeline -c unit_release_docker/unit_release_docker_pipeline.yml -l config.yml
fly -t ci-starter unpause-pipeline --pipeline full_pipeline
```

After that you can admire your pipeline in the web ui.

## Further Information
Each folder has it's own README.md which explains each pipeline shortly.


