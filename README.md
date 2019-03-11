# Build a Docker container for Tesseract4 and convert it to a Singularity container


Build a Tesseract container, push it to Dockerhub, and convert it 
to run as a Singularity container on Jetstream, Savio, or anywhere
else that you have the Singularity container runtime installed.

```bash
$ git clone https://github.com/ucb-rit/singularity-tesseract
$ cd singularity-tesseract
$ docker build --rm --tag tesseract .
$ docker tag tesseract:latest ucbrit/tesseract:latest
$ docker push ucbrit/tesseract:latest
$ singularity pull docker://ucbrit/tesseract:latest
```

To confirm that Tesseract was installed in the Docker container, run the following command (presumably before pushing the container to Docker Hub):

```bash
-->sudo docker run -it ucbrit/tesseract:latest tesseract --version
Tesseract Open Source OCR Engine v4.1.0-rc1-56-g7fbd with Leptonica
[...]
-->
```

Note the version of the installed application in the output above.

To test, shell into the Singularity container and check that Tesseract is running in the container:

```bash
$ singularity shell tesseract-lastest.simg
Singularity: Invoking an interactive shell within container...
[...] > tesseract --version
tesseract 4.0.0.beta.1
[...]
```

As of 08 August 2018, these instructions have been tested using Singularity version 2.6.0.

This repository was replicated from https://github.com/ucberkeley/brc-cyberinfrastructure/tree/master/tesseract-containerized on 2019-02-15.
