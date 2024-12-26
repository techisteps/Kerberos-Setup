# Use the official Ubuntu 24.04 image as the base
FROM archlinux:latest

# Set the maintainer information
# MAINTAINER Jai

# docker rm $(docker ps -aq)
# docker stop kssh && docker rm kssh && docker buildx build -t kssh:v1 .
# docker run -dit --net=krb5 --name kssh --hostname kssh.jai.net kssh:v1 /bin/bash
### docker attach kssh
### docker exec kssh nohup /usr/bin/sshd -D && docker exec kssh ps -ef
# docker exec kssh /setup-service.sh

RUN pacman -Sy --noconfirm krb5 openssh vi

COPY krb5.conf /etc/krb5.conf
COPY ssh_config /etc/ssh/ssh_config
COPY sshd_config /etc/ssh/sshd_config
COPY k5login /root/.k5login

COPY setup-service.sh /setup-service.sh
# CMD [ "/setup-service.sh" ]

# RUN mkdir /var/krb5kdc

### kadmin
### addprinc -randkey host/kssh.jai.net
### ktadd host/kssh.jai.net
# kadmin -w jai -q 'addprinc -randkey host/kssh.jai.net'
# kadmin -w jai -q 'ktadd host/kssh.jai.net'
# /usr/bin/ssh-keygen -A
# nohup /usr/bin/sshd -D -E /var/sshd.log &
# tail -f /var/sshd.log







# [root@kssh /]# cat /usr/lib/systemd/system/sshd.service
# [Unit]
# Description=OpenSSH Daemon
# Wants=sshdgenkeys.service
# After=sshdgenkeys.service
# After=network.target

# [Service]
# Type=notify-reload
# ExecStart=/usr/bin/sshd -D
# KillMode=process
# Restart=always

# [Install]
# WantedBy=multi-user.target


# [root@kssh /]# cat /usr/lib/systemd/system/sshdgenkeys.service
# [Unit]
# Description=SSH Key Generation
# ConditionPathExists=|!/etc/ssh/ssh_host_ecdsa_key
# ConditionPathExists=|!/etc/ssh/ssh_host_ecdsa_key.pub
# ConditionPathExists=|!/etc/ssh/ssh_host_ed25519_key
# ConditionPathExists=|!/etc/ssh/ssh_host_ed25519_key.pub
# ConditionPathExists=|!/etc/ssh/ssh_host_rsa_key
# ConditionPathExists=|!/etc/ssh/ssh_host_rsa_key.pub

# [Service]
# ExecStart=/usr/bin/ssh-keygen -A
# Type=oneshot

# [Install]
# WantedBy=multi-user.target