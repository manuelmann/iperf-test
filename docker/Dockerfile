FROM fedora:latest
MAINTAINER Manuel
RUN dnf install -y git gcc-c++ libstdc++ make
RUN git clone https://github.com/manuelmann/iperf2-test.git && cd iperf2-test && ./configure cflag=-static && make
COPY /iperf2-test/src/iperf /bin/iperf
RUN ldd /bin/iperf
ENTRYPOINT ["/bin/iperf"]
