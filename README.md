# RasaDocker

[![License]](https://github.com/jharrilim/RasaDocker/blob/master/LICENSE)
[![Readme]](https://github.com/jharrilim/RasaDocker#readme)
[![Docker Pulls]](https://hub.docker.com/r/josephharrisonlim/rasa)

## Build, Run, Publish

```sh
docker build -t josephharrisonlim/rasa:latest .
docker run --rm -it josephharrisonlim/rasa:latest
docker push josephharrisonlim/rasa:latest
```

## Dockerfile

```Dockerfile
FROM continuumio/anaconda3 as base
RUN  /bin/bash -cl " \
     apt-get install -y build-essential && \
     pip install --upgrade pip && \
     pip install tensorflow && \
     pip install rasa-x --extra-index-url https://pypi.rasa.com/simple && \
     conda install -y -c conda-forge portaudio && \
     conda install -y PyAudio && \
     conda install -y -c conda-forge speechrecognition"
CMD  ["/bin/bash", "-cl", "rasa"]
```

[License]: https://img.shields.io/github/license/jharrilim/RasaDocker?style=flat-square&logo=github
[Readme]: https://img.shields.io/badge/GitHub-Readme-blue?style=flat-square&logo=github
[Docker Pulls]: https://img.shields.io/docker/pulls/josephharrisonlim/rasa?style=flat-square&logo=docker
