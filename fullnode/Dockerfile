FROM  ubuntu
RUN mkdir /root/.waves
RUN mkdir /root/.waves/configs
RUN mkdir /root/.waves/src
WORKDIR /root/.waves
RUN apt-get update
RUN apt-get install -y default-jre default-jdk curl gnupg

RUN echo "deb https://dl.bintray.com/sbt/debian /" | tee -a /etc/apt/sources.list.d/sbt.list
RUN curl -sL "https://keyserver.ubuntu.com/pks/lookup?op=get&search=0x2EE0EA64E40A89B84B2DF73499E82A75642AC823" | apt-key add
RUN apt-get update
RUN apt-get install -y sbt

RUN git clone https://github.com/wavesplatform/Waves.git src
WORKDIR /root/.waves/src
RUN sbt checkPR
RUN sbt packageAll

RUN dpkg -i node/target/*.deb

HEALTHCHECK --interval=10s --timeout=3s --retries=3 CMD curl --fail http://0.0.0.0:6869/node/status || exit 1

# CMD [ "java", "-jar", "/root/.waves/src/node/target/waves-all*.jar", "/root/.waves/configs/waves-mainnet.conf" ]

EXPOSE 6868 6869