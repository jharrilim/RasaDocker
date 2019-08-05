# RasaDocker

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
