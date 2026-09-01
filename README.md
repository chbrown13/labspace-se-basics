# Overview

This workshop provides a high-level overview of several useful tools and activities for supporting software development work and skills to help you be productive as a software engineer.[^1] This interactive workshop uses [Docker Labspaces](https://hub.docker.com/extensions/dockersamples/labspace-extension). The goal of this workshop is for you practice and learn a set of relevant tools and processes for software engineering that will also be useful for this course. Please read the instructions for each section carefully for details on how to complete and submit your work.

## Launch the Labspace

> This labspace requires docker 19+, docker compose 2+, and the labspace extension installed with Docker Desktop running. If you are enrolled in a class with Dr. Brown, use `baker check CS3704/profile:labspace.yml` to ensure your environment is set up correctly.

To launch the Labspace, run the following command:

```bash
docker compose -f oci://chbrown13/labspace-se-basics up -d
```
or (specifically for Windows)

```bash
docker compose --project-directory . -f oci://chbrown13/labspace-se-basics up -d
```

And then open your browser to http://localhost:3030.


[^1]: The content of this workshop is primarily based on the [Engineering Basics](https://github.com/chrisparnin/EngineeringBasics) workshop by Dr. Chris Parnin.

