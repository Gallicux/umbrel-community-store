FROM arm64v8/debian:trixie-slim

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
      ca-certificates \
      libstdc++6 \
      tini \
 && rm -rf /var/lib/apt/lists/*

COPY bitcoinIId /usr/local/bin/bitcoinIId
COPY bitcoinII-cli /usr/local/bin/bitcoinII-cli
COPY bitcoinIId-wrapper.sh /usr/local/bin/bitcoinIId-wrapper.sh

RUN chmod 0755 \
      /usr/local/bin/bitcoinIId \
      /usr/local/bin/bitcoinII-cli \
      /usr/local/bin/bitcoinIId-wrapper.sh

EXPOSE 8337 8338 28336

ENTRYPOINT ["tini","--","/usr/local/bin/bitcoinIId-wrapper.sh"]

CMD ["-datadir=/data","-conf=/data/bitcoinII.conf"]
