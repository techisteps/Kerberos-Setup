# Run Kerberos Server Container

We need 3 components to test complete Kerberos setup. 
- Kerberos server
- Kerberos Client
- Some service which supports Kerberos authentication (In our case SSH service)

### Create an Docker image with Kerberos service installed.
```bash
cd /mnt/c/DevBox/kerberos/ubuntu/server
docker buildx build -t kserver:v1 .
```


### Below command will run container from image created in previous step.
> hostname is important because client will point this server for authentication
> Common network is also important so that all 3 containers can talk to each other.

```bash
docker run -dit --net=krb5 --name kserver --hostname kdc.jai.net kserver:v1 /bin/bash
```

Once container is started run below command to setup and start the Kerberos service.

```bash
docker exec kserver /setup-service.sh
```

### Create network if not already present
```bash
docker network create krb5
```


# Handy commands

```bash
# docker rm $(docker ps -aq)
docker rm kserver
docker attach kserver
docker start kserver
docker exec kserver service --status-all
```

apt-get update
DEBIAN_FRONTEND=noninteractive apt-get install -yq krb5-kdc krb5-admin-server


krb5kdc

-- krb5_newrealm

service --status-all

service krb5-kdc start
service krb5-kdc status

service krb5-admin-server start
service krb5-admin-server status



