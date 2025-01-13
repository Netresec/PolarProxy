# Rulesets for PolarProxy
[PolarProxy](https://www.netresec.com/?page=PolarProxy) can be used as a TLS firewall by providing a ruleset that defines match conditions and corresponding actions.

The rule based logic is activated by starting PolarProxy with `--ruleset FILE`, where `FILE` can be either a path or a URL to a ruleset file.

As an example, the following command will start an HTTPS proxy on port 8080 that blocks TLS traffic to malicious domains, but lets all other TLS traffic pass through without inspecting or decrypting the TLS layer:

`PolarProxy --httpconnect 8080 --ruleset https://raw.githubusercontent.com/Netresec/PolarProxy/main/rulesets/ruleset-block-malicious.json`

PolarProxy rulesets can also block ad and tracker traffic without having to install an adblocker in the browser. This command starts an HTTPS proxy that blocks ads and trackers:

`PolarProxy --httpconnect 8080 --ruleset https://raw.githubusercontent.com/Netresec/PolarProxy/main/rulesets/ruleset-block-ads.json`

For more information about the ruleset format, see [PolarProxy TLS Firewall](https://www.netresec.com/?page=TlsFirewall).
