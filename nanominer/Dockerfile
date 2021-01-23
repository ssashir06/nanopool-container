FROM ubuntu:20.04 as build
RUN apt-get update && \
    apt-get install -y curl && \
    apt-get clean

ARG DOWNLOAD_URL=https://github.com/nanopool/nanominer/releases/download/v3.1.5/nanominer-linux-3.1.5-cuda11.tar.gz
WORKDIR /app
RUN curl -Lo - "$DOWNLOAD_URL" | tar --strip-components 1 -zxf - 
RUN rm *.ini

FROM ubuntu:20.04
RUN useradd --user-group --system --create-home --no-log-init app
WORKDIR /app
RUN chown app:app /app
USER app
COPY --from=build /app /app