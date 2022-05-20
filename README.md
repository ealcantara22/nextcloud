## Nextcloud
Simple [nextcloud](https://nextcloud.com/) docker-compose configuration based on the [linuxserver](https://docs.linuxserver.io/images/docker-nextcloud) team image

### How to use it
1. copy the env.example file and replace the values 
   ```shell
    shell cp .env.example .env
   ```
2. create the external network if it doesn't exist
    ```shell
      docker network create <network-name>
    ```
3. start the container
   ```shell
     docker compose up -d
   ```
4. access https://<server-url:mapped-port> and follow the steps. The container 
generates a self-signed certificate but if you use a reverse proxy such as traefik you
can disable this check for the container, read how [here](https://docs.linuxserver.io/faq#strict-proxy).
5. Finally, allow external requests by including your server ip as a trusted domain
    ```shell
      nano <config volume path>/www/nextcloud/config/config.php
    ```
    ```shell
    # config.php
    'trusted_domains' =>
      array (
        0 => '...',
        1 => '<server-ip>',
      ),
    ```
