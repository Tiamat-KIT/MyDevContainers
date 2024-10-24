FROM mcr.microsoft.com/devcontainers/base:ubuntu

# ユーザー設定の引数
ARG USER_NAME=utakata
ARG USER_ID=1100
ARG GROUP_ID=1100

# 環境変数の設定
ENV DEBIAN_FRONTEND=noninteractive

# システムのアップデートと必要なパッケージのインストール
RUN apt-get update && apt-get install -y \
    curl \
    unzip \
    && rm -rf /var/lib/apt/lists/*

# ユーザーとグループの作成
RUN groupadd -g ${GROUP_ID} ${USER_NAME} && \
    useradd -m -u ${USER_ID} -g ${GROUP_ID} ${USER_NAME}

# デフォルトシェルをbashに設定
RUN chsh -s /bin/bash ${USER_NAME} \
    && echo 'export PS1="\e[01;32m\u\e[m:\e[01;34m\w\e[m\$ "' >> /home/${USER_NAME}/.bashrc

# ユーザーの切り替え
USER ${USER_NAME}
WORKDIR /home/${USER_NAME}

# Bunのインストール (ユーザー専用)
RUN curl -fsSL https://bun.sh/install | bash
ENV PATH="/home/${USER_NAME}/.bun/bin:${PATH}"
RUN echo 'export PATH="/home/${USER_NAME}/.bun/bin:$PATH"' >> /home/${USER_NAME}/.bashrc

# シェルの設定
SHELL ["/bin/bash", "-c"]