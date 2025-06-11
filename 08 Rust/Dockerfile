FROM rust:slim-bullseye AS builder

WORKDIR /app
COPY . .
RUN cargo build --release

FROM debian:bookworm-slim
RUN apt-get update \
    && apt-get install -y tini \ 
    && apt-get clean \ 
    && rm -rf /var/lib/apt/lists/*

RUN groupadd -r rustapp && useradd --no-log-init -r -g rustapp rustapp
COPY --from=builder --chown=rustapp:rustapp /app/target/release/hello /usr/local/bin/hello

USER rustapp
ENTRYPOINT ["tini","--"]
CMD ["hello"]
