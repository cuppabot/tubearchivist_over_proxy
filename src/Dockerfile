FROM bbilly1/tubearchivist

ARG PROXY

ADD patch /tmp/patch

RUN sed -i -- "s|PROXYHERE|${PROXY}|g" /tmp/patch/*.patch && \
    apt update && \
    apt install -y patch && \
    pip install --upgrade yt-dlp && \
    patch -p1 /app/home/src/ta/helper.py < /tmp/patch/helper.patch && \
    patch -p1 /app/home/src/download/thumbnails.py < /tmp/patch/thumbnails.patch && \
    patch -p1 /app/home/src/download/yt_dlp_base.py < /tmp/patch/yt_dlp_base.patch && \
    rm -rf /tmp/patch && \
    apt clean && \
    rm -rf /var/lib/apt/lists/*
