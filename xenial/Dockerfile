FROM ilmco/swift:4.1.2-xenial

RUN wget -qO - http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub | apt-key add -
COPY ./files/cuda.list /etc/apt/sources.list.d/
COPY ./files/cudnn.list /etc/apt/sources.list.d/

RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt install -yq --no-install-recommends \
      cuda-runtime-9-0 \
      libcudnn7 \
      libcudnn7-dev \
 && rm -rf /var/lib/apt/lists/* \
 && rm -rf /var/cache/apt/archives/*

ADD ./pkgs /tmp/pkgs
RUN apt-get install -yq --no-install-recommends /tmp/pkgs/*.deb

RUN swift --version
