# PolarProxy
Assets and resources for [PolarProxy](https://www.netresec.com/?page=PolarProxy).

<img src="PolarProxy_v2_2000x2000.webp" alt="PolarProxy logo" width="300" height="300" style="max-width: 30%; height: auto;" />

# Install as Container
Install docker container from command line:

`docker pull ghcr.io/netresec/polarproxy:latest`

Or better yet, use our [docker-compose.yml](docker-compose.yml) to install the docker container:
```
curl -fsSL https://raw.githubusercontent.com/Netresec/PolarProxy/refs/heads/main/polarproxy.env -o polarproxy.env
curl -fsSL https://raw.githubusercontent.com/Netresec/PolarProxy/refs/heads/main/docker-compose.yml -o docker-compose.yml
# Modify polarproxy.env if needed 
docker compose up -d
```


# PolarProxy Dockerfiles
For more information about how to run PolarProxy in Docker, see [PolarProxy in Docker](https://www.netresec.com/?page=Blog&month=2020-10&post=PolarProxy-in-Docker). We also have instructions for [deploying PolarProxy in Podman](https://www.netresec.com/?page=Blog&month=2020-10&post=PolarProxy-in-Podman).
