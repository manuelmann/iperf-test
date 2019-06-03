From registry.access.redhat.com/ubi7/ubi as builder
MAINTAINER manuelmann
RUN yum -y update
RUN yum install -y git gcc-c++ libstdc++ make
RUN git clone https://github.com/manuelmann/iperf2-test.git && cd iperf2-test && ./configure cflag=-static && make

FROM registry.access.redhat.com/ubi7/ubi
RUN yum install -y libstdc++
COPY --from=builder /iperf2-test/src/iperf /bin/iperf
CMD exec /bin/sh -c "trap : TERM INT; (while true; do sleep 1000; done) & wait"
#ENTRYPOINT ["/bin/iperf"]
