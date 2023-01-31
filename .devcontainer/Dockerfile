FROM rust:1.67.0-slim-bullseye
RUN rustup install nightly \
    && rustup component add rust-src --toolchain nightly \
    && cargo install cargo-dylint dylint-link \
    && cargo install cargo-contract --force
WORKDIR /root/
ADD .bashrc /root/.bashrc
RUN wget https://github.com/WebAssembly/binaryen/releases/download/version_111/binaryen-version_111-x86_64-linux.tar.gz -P /root/ \
    && tar -xzf /tmp/binaryen-version_111-x86_64-linux.tar.gz --directory /root/ \
    && cp -a /root/binaryen-version_111/bin/* /usr/bin/ \
    && rm -Rf /root/binaryen-version_111*
ENV DEBIAN_FRONTEND=noninteractive
RUN apt update -y && apt upgrade -y && apt install -y vim less locate \
    && rm -rf /var/lib/apt/lists/* && updatedb \
    && mkdir /root/contracts/ 

