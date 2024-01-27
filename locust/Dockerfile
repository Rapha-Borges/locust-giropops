FROM cgr.dev/chainguard/python:latest-dev@sha256:6d42e7b0b3663ef9f99e33ab98058d853c1b79eae8af62c21d7784ca06242c5d as builder

USER root

RUN apk --no-cache add build-base

COPY requirements.txt .

RUN pip install --prefix="/reqs" -r requirements.txt

FROM cgr.dev/chainguard/python:latest@sha256:fe4740c2caa7ee0bb8a7da188630a4188b33692ce21d71cf30488dcfd570e4a8
WORKDIR /usr/src/app
VOLUME /usr/src/app/scripts
COPY --from=builder /reqs /usr/local
ENTRYPOINT locust
