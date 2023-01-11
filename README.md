
## Docker setup

### Ubuntu 20.04 / Ubuntu 22.04 

``` 
    sudo apt install gnome-terminal
    sudo apt remove docker-desktop
```
Uninstall the tech preview or beta version of Docker Desktop for Linux. Run:
```
    rm -r $HOME/.docker/desktop
    sudo rm /usr/local/bin/com.docker.cli
    sudo apt purge docker-desktop
```

#### Set up the repository

1. Update the apt package index and install packages to allow apt to use a repository over HTTPS:
```
    sudo apt-get update
    sudo apt-get install \
        ca-certificates \
        curl \
        gnupg \
        lsb-release
```
2. Add Docker’s official GPG key:

```
    sudo mkdir -p /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

3. Use the following command to set up the repository:
```
  echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Download the docker desktop [deb package](https://desktop.docker.com/linux/main/amd64/docker-desktop-4.15.0-amd64.deb?utm_source=docker&utm_medium=webreferral&utm_campaign=docs-driven-download-linux-amd64)

```
    sudo apt-get update
    sudo apt-get install ./docker-desktop-<version>-<arch>.deb
```

### Build the containers

Please edit ***.env*** file to change postgres user, password and GitHub user details. Then do the following
```
   cd projects/sf-docker-postgres
   docker compose up -d --buid
```

Have a coffee, relax and wait it to build containers

### pgAdmin Installation  (Optional)

You can install pgAdmin to monitor postgres database by downloading it from [here](https://www.pgadmin.org/)







