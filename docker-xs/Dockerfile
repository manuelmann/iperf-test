FROM alpine:latest
MAINTAINER manuel
RUN apk update
RUN apk add g++ gcc make git
RUN git clone https://github.com/manuelmann/iperf2-test.git && cd iperf2-test && ./configure cflag=-static && make

FROM alpine:latest
RUN apk update
RUN apk add bash
COPY --from=0 /iperf2-test/src/iperf /bin/iperf
RUN ldd /bin/iperf
WORKDIR /bin/
