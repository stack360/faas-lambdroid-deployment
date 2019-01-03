faas-mq-deployment
==============

### Prerequisites:
 - docker
 - docker swarm
 - docker compose

### How to use this code:
Run following commands to generate secrets

```shell
    echo "admin" | docker secret create basic-auth-user -
    secret=$(head -c 16 /dev/urandom| $sha_cmd | cut -d " " -f 1)
    echo "$secret" | docker secret create basic-auth-password -
    echo "[Credentials]\n username: admin \n password: $secret\n echo -n "$secret" | faas-cli login --username=admin --password-stdin"
```

Then run `docker stack deploy --compose-file docker-compose.yml faas-mq`
