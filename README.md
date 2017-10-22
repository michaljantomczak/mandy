Mandy
========================

Welcome to the Mandy device management system.

Set development environment
========================
Required
---------
- docker

Install:
--------
Execute command in shell.

    docker-compose up --build -d
    
Connect to container:

    docker exec -it {container-hash} /bin/bash

Install vendors:

    php /composer.phar install
    
