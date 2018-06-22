# Docker MFTF
Docker images for Magento Functional Testing Framework (MFTF)

## Docker Service
### Install
[Docker](https://docs.docker.com/install/)
[Docker Compose](https://docs.docker.com/compose/install/)

**Note for Windows**
To run command in Windows, please use linux simulator.

For example, via `docker`
```sh
docker build -t compose .
docker run --rm -it -v //var/run/docker.sock:/var/run/docker.sock \
  -v $(pwd):/dockermftf -w /dockermftf --network host compose
```

Or use a virtual machine

### Build Images
```sh
sudo bin/build
```

### Run Services
```sh
sudo bin/run
```

## SSH
```sh
docker exec -u {username} -it {container_name} /bin/bash
```

## Run Test
### Acceptance
After `ssh` to docker container `mftf` with username `www-data`
```sh
docker exec -u www-data -it dockermftf_mftf_1 /bin/bash
cd dev/tests/acceptance
vendor/bin/robo generate:tests
vendor/bin/codecept run
```

[magento functional testing framework](https://devdocs.magento.com/guides/v2.2/magento-functional-testing-framework/release-2/getting-started.html)

[codeception](https://codeception.com/docs/02-GettingStarted)

### Functional
After `ssh` to docker container `mftf` with username `www-data`
```sh
docker exec -u www-data -it dockermftf_mftf_1 /bin/bash
cd dev/tests/functional
php utils/generate.php
vendor/bin/phpunit
```

[magento testing framework](https://devdocs.magento.com/guides/v2.2/mtf/mtf_quickstart/mtf_quickstart_runtest.html)

### API Functional
```sh
cd dev/tests/api-functional
../functional/vendor/bin/phpunit
```

### Integration
```sh
apt-get update && apt-get install mysql-client

cd dev/tests/integration
../functional/vendor/bin/phpunit
```

## VNC Viewer
```sh
vncviewer localhost:5900
```
Password: `secret`

## Magento Site
[https://localhost.com/admin/](https://localhost.com/admin/)
admin/admin123
