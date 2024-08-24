FROM debian:latest

RUN apt-get update && \
    apt-get install -y icecast2 mime-support && \
    rm -rf /var/lib/apt/lists/*

RUN useradd -m icecastuser

RUN mkdir -p /var/lib/icecast2 /var/log/icecast2 && \
    chown -R icecastuser:icecastuser /var/lib/icecast2 /var/log/icecast2 /etc/icecast2

COPY icecast.xml /etc/icecast2/icecast.xml

EXPOSE 8000

USER icecastuser

ENTRYPOINT ["/usr/bin/icecast2", "-n", "-c", "/etc/icecast2/icecast.xml"]
