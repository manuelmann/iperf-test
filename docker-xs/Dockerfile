FROM alpine:latest AS builder
MAINTAINER manuelmann
RUN apk update
RUN apk add g++ gcc make git
RUN git clone https://github.com/manuelmann/iperf2-test.git && cd iperf2-test && ./configure cflag=-static && make

FROM alpine:latest
RUN apk add bash
COPY --from=builder /lib/ld-musl-x86_64.so.1 /lib/ld-musl-x86_64.so.1
COPY --from=builder /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.6
COPY --from=builder /usr/lib/libgcc_s.so.1 /usr/lib/libgcc_s.so.1
COPY --from=builder /lib/ld-musl-x86_64.so.1 /lib/ld-musl-x86_64.so.1
COPY --from=builder /iperf2-test/src/iperf /bin/iperf
CMD exec /bin/sh -c "trap : TERM INT; (while true; do sleep 1000; done) & wait"
#ENTRYPOINT ["/bin/iperf"]
