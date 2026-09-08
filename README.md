# PolarProxy
[PolarProxy](https://www.netresec.com/?page=PolarProxy) is a transparent TLS and SSL inspection proxy created for incident responders, malware analysts and security researchers. PolarProxy decrypts and re-encrypts TLS traffic, while also saving the decrypted traffic in a PCAP file that can be loaded into Wireshark or an intrusion detection system (IDS). 

<img src="PolarProxy_v2_2000x2000.webp" alt="PolarProxy logo" width="300" height="300" style="max-width: 30%; height: auto;" />

More information about PolarProxy can be found on the [PolarProxy website](https://www.netresec.com/?page=PolarProxy).

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

# Environment Variables

The following environment variables can be set to configure PolarProxy.

```
PP_AUTOFLUSH
PP_BYPASS
PP_BYPASSEXACT
PP_BYPASSONFAIL
PP_CACERT
PP_CERTHTTP
PP_CLIENTCERT
PP_CONNECT
PP_CUTOFF
PP_DEBUG
PP_EXPORT
PP_FLOWLOG
PP_HAPROXY
PP_HELP
PP_HELPENV
PP_HELPHTML
PP_HTTPCONNECT
PP_IDLETIMEOUTCLIENT
PP_IDLETIMEOUTSERVER
PP_KEY
PP_KEYFILE
PP_LEAFCERT
PP_MSS
PP_NONTLS
PP_NOSNI
PP_OUTPUTDIR
PP_PCAPOVERIP
PP_PCAPOVERIPCONNECT
PP_PCAPOVERIPPRIVATE
PP_PROXY
PP_REDIRECT
PP_RULESET
PP_SOCKS
PP_TERMINATE
PP_TIMEOUT
PP_TLSTIMEOUT
PP_VERBOSE
PP_WRITE
PP_WRITEALL
```

# PolarProxy Dockerfiles
For more information about how to run PolarProxy in Docker, see [PolarProxy in Docker](https://www.netresec.com/?page=Blog&month=2020-10&post=PolarProxy-in-Docker). We also have instructions for [deploying PolarProxy in Podman](https://www.netresec.com/?page=Blog&month=2020-10&post=PolarProxy-in-Podman).
