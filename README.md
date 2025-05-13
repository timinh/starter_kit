# Starter Kit For Php projects

# What's included
- A compose.yaml file for a local dev environment with a preconfigured stack :
    - frankenphp with a default Caddyfile (drop it to get a default symfony config with mercure)
    - mariadb
    - (nodejs)
    - (maildev)

# How to use

**clone the repository :**

```bash
git clone https://github.com/timinh/starter_kit.git my_project && rm -Rf my_project/.git
```

**then cd into the project folder :**

```bash
cd my_project
```

start the docker stack : 

**linux :**
```bash
make start
```
**windows**

```dos
docker compose up -d -f deployments/local/compose.yaml
```
Or in your IDE, right click on the **compose.yaml** in the *deployments/local* folder and select **compose up**

# Add services

In the *deployments/local/compose.yaml* file add : 

## maildev
```yaml
    ###> maildev ###
    maildev:
        extends:
            file: ../services/maildev.yaml
            service: maildev-local
    ### maildev ###
```

## nodejs
```yaml
    ###> nodejs ###
    nodejs:
        extends:
            file: ../services/nodejs.yaml
            service: nodejs-local
    ### nodejs ###
```

# Run commands in containers

Access the app container in bash : 
```bash
make bash
```

The database container : 
```bash
make bash-db
```

The front container (for node packages installation or removal) :
```bash
make bash-front
```
