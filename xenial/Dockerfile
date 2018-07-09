FROM ilmco/swift:4.1.2-xenial

RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get install -yq \
      apt-transport-https \
 && rm -rf /var/lib/apt/lists/* \
 && rm -rf /var/cache/apt/archives/*

RUN curl -s http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub | apt-key add -
RUN curl -ks https://f88d67a620f77d476c3eda050e144e9e6816428e@raw.githubusercontent.com/ilmco/apt-repo/master/A57CDE0A4A89C597.pub | apt-key add -
COPY ./files/*.list /etc/apt/sources.list.d/

RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt install -yq --no-install-recommends \
      cuda-runtime-9-0 \
      cuda-misc-headers-9-0 \
      libcudnn7 \
      libcudnn7-dev \
      libvisionworks \
      libvisionworks-dev \
      libnvinfer4 \
      libnvinfer-dev \
 && rm -rf /var/lib/apt/lists/* \
 && rm -rf /var/cache/apt/archives/*


ADD ./pkgs /tmp/pkgs
RUN apt-get install -yq --no-install-recommends /tmp/pkgs/*.deb

RUN swift --version
