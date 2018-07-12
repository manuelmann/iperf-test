FROM alpine:latest
MAINTAINER manuel
RUN apk update
RUN apk add g++ gcc make git bash
RUN git clone https://github.com/manuelmann/iperf2-test.git && cd iperf2-test && ./configure cflag=-static && make
COPY /iperf2-test/src/iperf /bin/iperf
RUN ldd /bin/iperf
WORKDIR /bin/
