# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.234.0/containers/ubuntu/.devcontainer/base.Dockerfile

# [Choice] Ubuntu version (use ubuntu-22.04 or ubuntu-18.04 on local arm64/Apple Silicon): ubuntu-22.04, ubuntu-20.04, ubuntu-18.04
ARG VARIANT="jammy"
FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

ARG PYTHON_VER="3.9.12"

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>


RUN mkdir /install && cd /install && \
    curl -LO https://github.com/aws/aws-sam-cli/releases/latest/download/aws-sam-cli-linux-x86_64.zip && \
    unzip aws-sam-cli-linux-x86_64.zip -d sam-installation && \
    ./sam-installation/install &&\
    cd $HOME && rm -Rf /install

RUN apt update && apt install -y git build-essential zlib1g-dev libssl-dev \
    libbz2-dev libffi-dev libsqlite3-dev libreadline-dev python3-pip

RUN curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
RUN sudo apt-get install -y nodejs yarn && npm install -g @aws-amplify/cli aws-cdk


USER vscode:vscode
WORKDIR /home/vscode
ENV PYENV_ROOT=/home/vscode/.pyenv
ENV PATH=$PYENV_ROOT/shims:$PYENV_ROOT/bin:$PATH
RUN mkdir -p /home/vscode/.local/bin && \
    pip install -U pipenv && \
    curl https://pyenv.run | bash && \
    echo 'eval "$(pyenv init -)"' >> /home/vscode/.bashrc && \
    echo 'eval "$(pyenv virtualenv-init -)"' >> /home/vscode/.bashrc && \
    eval "$(pyenv init -)" && \
    pyenv install ${PYTHON_VER} && \
    pyenv global ${PYTHON_VER}