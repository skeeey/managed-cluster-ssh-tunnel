FROM alpine

RUN apk update && \
    apk add --no-cache openssh && \
    apk add --no-cache openssh-server-pam && \
    sed -i "s/#PasswordAuthentication.*/PasswordAuthentication no/g" /etc/ssh/sshd_config && \
    sed -i "s/#ChallengeResponseAuthentication.*/ChallengeResponseAuthentication no/g" /etc/ssh/sshd_config && \
    sed -i "s/#UsePAM.*/UsePAM yes/g" /etc/ssh/sshd_config && \
    sed -i "s/AllowTcpForwarding.*/AllowTcpForwarding yes/g" /etc/ssh/sshd_config && \
    sed -i "s/GatewayPorts.*/GatewayPorts yes/g" /etc/ssh/sshd_config && \
    ssh-keygen -t dsa -P "" -f /etc/ssh/ssh_host_dsa_key && \
    ssh-keygen -t rsa -P "" -f /etc/ssh/ssh_host_rsa_key && \
    ssh-keygen -t ecdsa -P "" -f /etc/ssh/ssh_host_ecdsa_key && \
    ssh-keygen -t ed25519 -P "" -f /etc/ssh/ssh_host_ed25519_key

RUN  adduser -D tunnel && \
     mkdir -p /home/tunnel/.ssh && \
     chmod 700 /home/tunnel/.ssh

COPY id_rsa.pub /home/tunnel/.ssh/authorized_keys

RUN chown -R tunnel:tunnel /home/tunnel/.ssh
