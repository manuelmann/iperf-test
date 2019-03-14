FROM fedora:latest AS builder
MAINTAINER Manuel

RUN dnf -y install git gcc-c++ libstdc++ make
RUN git clone https://github.com/manuelmann/iperf2-test.git && cd iperf2-test && ./configure cflag=-static && make

FROM fedora:latest
RUN dnf -y install bash tcpdump net-tools iftop vnstat
COPY --from=builder /lib/ld-musl-x86_64.so.1 /lib/ld-musl-x86_64.so.1
COPY --from=builder /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.6
COPY --from=builder /usr/lib/libgcc_s.so.1 /usr/lib/libgcc_s.so.1
COPY --from=builder /lib/ld-musl-x86_64.so.1 /lib/ld-musl-x86_64.so.1
COPY --from=builder /iperf2-test/src/iperf /bin/iperf

#ENTRYPOINT ["/bin/iperf"]
