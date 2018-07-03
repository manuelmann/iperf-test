FROM fedora:latest
MAINTAINER Manuel

RUN dnf install -y gcc-c++ git make

RUN git clone https://github.com/manuelmann/iperf2-test.git && cd iperf2-test && ./configure && make

FROM fedora:latest
COPY --from=0 /iperf2-test/src/iperf /bin/iperf
ENTRYPOINT ["/bin/iperf"]
