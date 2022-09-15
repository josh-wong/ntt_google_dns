<h1 align="center">
  <br>
  <a href=https://upload.wikimedia.org/wikipedia/commons/e/ee/NTT_company_logo.svg"><img src="https://upload.wikimedia.org/wikipedia/commons/e/ee/NTT_company_logo.svg"></a>
  <br>
  NTT x Google DNS
  <br>
</h1>


<p align="center">
  <a href="#modules">Modules</a> •
  <a href="#code-design">Code Design</a> •
  <a href="#install">Install</a> •
  <a href="#docker">Docker</a> •
  <a href="#pythonenv">PythonEnv</a> •
  <a href="#how-to-use">How To Use</a> •
</p>

This Google DNS package consists of :
- A NTT router IP parser to update dynamic DNS on google domains .

## Modules

At a granular level, Gnutools is a library that consists of the following components:

| Component | Description |
| ---- | --- |
| **google_dns** | Contains the implementation of GoogleDNS |


# Code structure
```python
from setuptools import setup
from gnutools import __version__

setup(
    name="google_dns",
    version=__version__,
    packages=[
        "google_dns",
    ],
    url="https://github.com/JeanMaximilienCadic/google_dns",
    license="MIT",
    author="Jean Maximilien Cadic",
    long_description="".join(open("README.md", "r").readlines()),
    long_description_content_type="text/markdown",
    python_requires=">=3.6",
    install_requires=[r.rsplit()[0] for r in open("requirements.txt")],
    author_email="git@cadic.jp",
    description="Google DNS",
    classifiers=[
        "Programming Language :: Python :: 3.6",
        "License :: OSI Approved :: MIT License",
    ],
)
```

## Install
To clone and run this application, you'll need [Git](https://git-scm.com) and [ https://docs.docker.com/docker-for-mac/install/]( https://docs.docker.com/docker-for-mac/install/) and Python installed on your computer. 
From your command line:

Install the package:
```bash
# Clone this repository and install the code
git clone https://github.com/JeanMaximilienCadic/ntt_google_dns

# Go into the repository
cd ntt_google_dns
```

## Config file
Create a config file at the root of this repo

```yaml
project: google_dns
url: 'http://[YOUR ROUTER IP]/ntt/information/fifth/current'
authorization: "dXNlcjphZG1pbg=="
cookie: 'HGWSESSIONID=1hoa40gjlzl2g'

hostnames:
- hostname: "mywebsite.com"
  google_id: "ksfjIkmldslI"
  google_password: 'sdk11kjl1jd'

```

## Makefile
Exhaustive list of make commands:
```
build_dockers
build_docker
push_dockers
push_docker
pull_dockers
pull_docker
docker_run
checkout
all
all_branch
```
## Docker
(\* recommended)

To build and run the docker image
```
make build_docker
make docker_run
```

## PythonEnv
(\* not recommended)
```
python setup.py install 
```

## How to
* Run the cron job
```shell
python -m google_dns
```
