FROM ubuntu:24.04


ARG VERSION=0.1.1
ARG CHECKSUM=30d9424df1eddb73912b0e2ad5375fa2c876c8e30906bec91952dfb75dcf220b

WORKDIR /app

RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    python3-venv \
    && rm -rf /var/lib/apt/lists/*

ADD --checksum=sha256:${CHECKSUM} https://github.com/MrDave/StaticJinjaPlus/archive/refs/tags/${VERSION}.tar.gz /tmp/app.tar.gz

RUN tar xzf /tmp/app.tar.gz --strip-components=1 -C /app && rm /tmp/app.tar.gz
RUN python3 -m venv venv && \
    . venv/bin/activate && \
    pip install --upgrade pip && \
    pip install -r requirements.txt --no-cache-dir

ENTRYPOINT ["/app/venv/bin/python3", "main.py", "-w"]

CMD ["--srcpath=/app/templates/", "--outpath=/app/build/"]