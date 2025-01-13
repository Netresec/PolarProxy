# Rulesets for PolarProxy
[PolarProxy](https://www.netresec.com/?page=PolarProxy) can be used as a TLS firewall by providing a ruleset that defines match conditions and corresponding actions.

The rule based logic is activated by starting PolarProxy with `--ruleset FILE`, where `FILE` can be either a path or a URL to a ruleset file.

As an example, the following command will start a SOCKS proxy on port 1080 that blocks TLS traffic to malicious domains, but lets all other traffic pass through without inspecting or decrypting the TLS layer:

`PolarProxy --socks 1080 --ruleset https://github.com/Netresec/PolarProxy/raw/refs/heads/main/rulesets/ruleset-block-malicious.json`

For more information about the ruleset format, see [PolarProxy TLS Firewall](https://www.netresec.com/?page=TlsFirewall).
