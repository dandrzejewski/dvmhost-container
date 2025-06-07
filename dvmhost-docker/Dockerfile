#
# Container for DVMHost
#


# ---- Update OS and install packages ----
FROM debian:bookworm AS os

RUN apt update && apt upgrade -y && apt install -y build-essential git libasio-dev libncurses-dev libssl-dev cmake

# ---- Set up the build environment ----
FROM os AS setup

RUN mkdir /build
WORKDIR /build
RUN git clone https://github.com/DVMProject/dvmhost.git
WORKDIR /build/dvmhost
RUN mkdir build

# ---- Build the application
FROM setup AS builder

WORKDIR /build/dvmhost/build
RUN cmake -DENABLE_TUI_SUPPORT=0 ..
RUN make -j$(($(nproc) / 2)) dvmhost

# ---- Slim down and build the final image ----
FROM debian:bookworm-slim AS runtime

RUN apt update && apt install -y libssl-dev

RUN mkdir /config
COPY --from=builder /build/dvmhost/build/dvmhost /usr/local/bin/
CMD ["/usr/local/bin/dvmhost", "-f", "-c", "/config/dvmhost.yml"]

