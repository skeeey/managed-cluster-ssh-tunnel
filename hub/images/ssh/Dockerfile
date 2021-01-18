FROM alpine
RUN apk update && \
    apk add --no-cache openssh-client

COPY id_rsa.pub /root/.ssh/id_rsa.pub
COPY id_rsa /root/.ssh/id_rsa
