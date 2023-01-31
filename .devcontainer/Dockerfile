FROM rust:1.67.0-bullseye
WORKDIR /root/
ADD .bashrc /root/.bashrc
ENV DEBIAN_FRONTEND=noninteractive
RUN apt update -y && apt upgrade -y \ 
    && apt install -y libssl-dev pkg-config tar wget vim less
RUN wget https://github.com/WebAssembly/binaryen/releases/download/version_111/binaryen-version_111-x86_64-linux.tar.gz -P /root/ \
    && tar -xzf /root/binaryen-version_111-x86_64-linux.tar.gz --directory /root/ \
    && cp -a /root/binaryen-version_111/bin/* /usr/bin/ \
    && rm -Rf /root/binaryen-version_111* \
    && mkdir /root/contracts/ 
RUN rustup install nightly \
    && rustup component add rust-src --toolchain nightly \
    && cargo install cargo-dylint dylint-link \
    && cargo install cargo-contract --force
RUN curl -fsSL https://deb.nodesource.com/setup_19.x \
    | bash - && apt-get install -y nodejs \
    && npm install --global yarn