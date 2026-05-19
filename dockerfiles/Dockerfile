#Based on https://github.com/dotnet/dotnet-docker/blob/main/src/runtime-deps/10.0/alpine3.23/amd64/Dockerfile
#Based on https://netresec.com/?b=20Accbd
FROM alpine:3.23

ENV \
    # UID of the non-root user and group 'polarproxy'
    APP_UID=57012 \
    # Enable detection of running in a container
    DOTNET_RUNNING_IN_CONTAINER=true \
    # Set the invariant mode since ICU package isn't included (see https://github.com/dotnet/announcements/issues/20)
    DOTNET_SYSTEM_GLOBALIZATION_INVARIANT=true

RUN apk add --upgrade --no-cache \
    ca-certificates-bundle \
    # .NET dependencies
    libgcc \
    libssl3 \
    libstdc++ \
    # manually update zlib from alpine base image
    zlib \
    # curl is required for healthcheck in docker-compose
    curl

# Create non-root user with home dir
RUN addgroup --gid=${APP_UID} polarproxy \
    && adduser --uid=${APP_UID} --ingroup=polarproxy --disabled-password --home /home/polarproxy polarproxy \
    && mkdir -p /home/polarproxy/.local/share \
    && chown -R ${APP_UID}:${APP_UID} /home/polarproxy \
    && mkdir -p /var/log/polarproxy \
    && chown polarproxy:polarproxy /var/log/polarproxy
    
VOLUME ["/var/log/polarproxy/", "/home/polarproxy/"]

# Copy binary
COPY --chown=${APP_UID}:${APP_UID} PolarProxy /usr/local/bin/PolarProxy
RUN chmod 0755 /usr/local/bin/PolarProxy

USER ${APP_UID}:${APP_UID}
WORKDIR /home/polarproxy

#Transparent TLS proxy: -p 10443,80,443
EXPOSE 10443/tcp
#SOCKS4/SOCKS4a/SOCKS5 server: --socks 1080
EXPOSE 1080/tcp
#HTTP Proxy server: --httpconnect 8080
EXPOSE 8080/tcp
#Web server hosting root CA X.509 certificate: --certhttp 10080
EXPOSE 10080/tcp
#PCAP-over-IP sever for decrypted traffic: --pcapoverip 57012
EXPOSE 57012/tcp

ENTRYPOINT ["/usr/local/bin/PolarProxy"]
CMD ["-p", "10443,80,443", "--socks", "1080", "--httpconnect", "8080", "--nontls", "allow", "--certhttp", "10080", "-x", "/var/log/polarproxy/polarproxy.cer", "-f", "/var/log/polarproxy/proxyflows.log", "--pcapoverip", "0.0.0.0:57012", "-o", "/var/log/polarproxy/", "-v"]
