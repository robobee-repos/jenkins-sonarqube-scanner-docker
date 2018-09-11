FROM debian:stretch-slim
LABEL maintainer "Erwin Mueller <erwin.mueller@deventm.com>"

ARG APT_CACHE

RUN set -x \
  # Optional add proxy entries for apt.
  && if [ -n "${APT_CACHE}" ]; then \
  echo Acquire::ftp::Proxy \"$APT_CACHE\"; >> /etc/apt/apt.conf.d/08proxy;\
  echo Acquire::http::Proxy \"$APT_CACHE\"; >> /etc/apt/apt.conf.d/08proxy;\
  echo Acquire::https::Proxy \"$APT_CACHE\"; >> /etc/apt/apt.conf.d/08proxy;\
  fi

RUN set -x \
  && DEBIAN_FRONTEND=noninteractive \
  && apt-get update \
  && apt-get install -y wget unzip \
  && rm -rf /var/lib/apt/lists/*

RUN set -x \
  && cd /tmp \
  && wget -O sonar-scanner-cli.zip https://sonarsource.bintray.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-3.2.0.1227-linux.zip \
  && unzip sonar-scanner-cli.zip \
  && mv sonar-scanner-3.2.0.1227-linux sonar-scanner \
  && mv sonar-scanner /opt

ENV SONAR_SCANNER_CLI="/opt/sonar-scanner/bin/sonar-scanner"

CMD ["/opt/sonar-scanner/bin/sonar-scanner", "--version"]
