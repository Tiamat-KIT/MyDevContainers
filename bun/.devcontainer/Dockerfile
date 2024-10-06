FROM mcr.microsoft.com/vscode/devcontainers/base:ubuntu-20.04

RUN set -x \
    && ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
    && echo 'Asia/Tokyo' >/etc/timezone

    # bun
ARG BUN_VERSION=1.1.2
RUN set -x \
    && curl -fsSL https://bun.sh/install | sudo -u ${USERNAME} bash -s "bun-v${BUN_VERSION}"

ARG USER_NAME=utakata
ARG USER_ID=1100
ARG GROUP_ID=1100 

RUN groupadd -g ${GROUP_ID} ${USER_NAME} && \
    useradd -m -u ${USER_ID} -g ${GROUP_ID} ${USER_NAME}


# デフォルトシェルをbashに設定
RUN chsh -s /bin/sh ${USER_NAME}

RUN apt-get update -y \
    && apt-get -y upgrade -y \
    && apt-get -y install --no-install-recommends \
    git \
    nano \
    vim-tiny \
    && apt-get auto-remove -y \
    && apt-get clean -y \
    && chsh -s $(which bash) bun \
    && echo 'export PS1="\e[01;32m\u\e[m:\e[01;34m\w\e[m\$ "' >> /home/bun/.bashrc

USER ${USER_NAME}