# FROM debian:sid
FROM ghcr.io/onedr0p/alpine:3.17.3

ENV BW_CLI_VERSION=2023.7.0

# RUN apt update && \
#     apt install -y wget unzip && \
#     wget https://github.com/bitwarden/clients/releases/download/cli-v${BW_CLI_VERSION}/bw-linux-${BW_CLI_VERSION}.zip && \
#     unzip bw-linux-${BW_CLI_VERSION}.zip && \
#     chmod +x bw && \
#     mv bw /usr/local/bin/bw && \
#     rm -rfv *.zip

RUN \
    curl -fsSL -o /tmp/app.zip "https://github.com/bitwarden/clients/releases/download/cli-v${BW_CLI_VERSION}/bw-linux-${BW_CLI_VERSION}.zip" \
    && unzip -q /tmp/app.zip -d /app \
    && chown -R root:root /app \
    && chmod -R 755 /app \
    && rm -rf /tmp/*


USER kah
COPY ./apps/bitwarden-cli/entrypoint.sh /entrypoint.sh
CMD ["/entrypoint.sh"]

LABEL org.opencontainers.image.source="https://github.com/bitwarden/clients"