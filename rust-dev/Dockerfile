# TO BUILD use:
#   docker build -t latrokles/dev-rust-stable .

# TO RUN use: 
#   docker run -it \
#          -v ~/workspace:/home/user/workspace \
#          -v ~/vim:/home/user/.vim \
#          --name dev-rust \
#          latrokles/dev-rust-stable

FROM latrokles/base-dev-env:latest

ENV RUST_VERSION 1.2.0
ENV RUST_BINARIES $HOME/rust-binaries
RUN mkdir $RUST_BINARIES
USER root
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
    build-essential \
    ca-certificates \
    libssl-dev && \
    cd $RUST_BINARIES && \
    curl -sO https://static.rust-lang.org/dist/rust-$RUST_VERSION-x86_64-unknown-linux-gnu.tar.gz && \
    tar -xzf $RUST_BINARIES/rust-$RUST_VERSION-x86_64-unknown-linux-gnu.tar.gz && \
    $RUST_BINARIES/rust-$RUST_VERSION-x86_64-unknown-linux-gnu/install.sh && \
    DEBIAN_FRONTEND=noninteractive apt-get remove --purge -y curl && \
    DEBIAN_FRONTEND=noninteractive apt-get autoremove -y 

USER latrokles
