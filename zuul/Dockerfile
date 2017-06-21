FROM debian:jessie

MAINTAINER Gabor Lekeny <gabor.lekeny@gmail.com>

RUN apt-get update && \
    apt-get install --yes --no-install-recommends \
        gcc \
        libyaml-dev \
        python \
        python-dev \
        python-pip && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/

RUN pip install -U pip && \
    pip install zuul

RUN mkdir -p /git \
             /etc/zuul \
             /var/lib/zuul/times

COPY etc/       /etc/zuul/
COPY ssh/id_rsa /root/.ssh/

CMD ["/usr/local/bin/zuul-server", "-d"]
