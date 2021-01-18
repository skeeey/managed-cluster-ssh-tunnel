FROM alpine

RUN apk update && \
    apk add --no-cache bind-tools && \
    apk add --no-cache curl

COPY get-pods /bin
