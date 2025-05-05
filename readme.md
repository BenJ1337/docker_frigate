# Frigate with Tapo C200
https://www.tp-link.com/us/home-networking/cloud-camera/tapo-c200/#specifications

## Setup
### Tapo camera
#### Create a camera account within the tapo App
https://www.tapo.com/en/faq/76/

### Docker-Compose
#### Docker Secrets
 - create the files for the secrets as specified in the docker compose file or change it to your liking

*Default:*
- create directory `$ mkdir ~/frigate-secrets/`
- create files for the secrets: e.g. `$ nano ~/frigate-secrets/c200-user.secret`

### Nginx as Reverse Proxy
#### Setup TLS for Nginx Reverse Proxy
```
$ mkdir ~/test-cert
$ openssl req -x509 -newkey rsa:4096 -keyout ~/test-cert/key.pem -out ~/test-cert/cert.pem -sha256 -days 3650 -nodes -subj "/C=/ST=/L=/O=/OU=/CN="
```

### Frigate
You may disable MQTT in `frigate.yml` if you don't need it.
```yaml
mqtt:
  enabled: false
```

## Start service

```
$ docker-compose up -d
```
