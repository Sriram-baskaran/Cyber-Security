# Recon-ng: Subdomain Enumeration

In terminal of Kali linux type recon-ng

## Objective

Perform passive reconnaissance to discover publicly accessible subdomains and associated infrastructure of a target domain.

## Target

certifiedhacker.com

## Module Used

recon/domains-hosts/hackertarget

## Commands Used

```bash
modules load recon/domains-hosts/hackertarget
options set SOURCE certifiedhacker.com
run
show hosts
dashboard
```

## Methodology

1. Loaded the Hackertarget module in Recon-ng.
2. Configured the target domain as `certifiedhacker.com`.
3. Executed the module to enumerate subdomains and associated IP addresses.
4. Stored the results in Recon-ng's hosts database.
5. Reviewed the findings using `show hosts` and `dashboard`.

## Findings

* Discovered 38 publicly accessible hosts.
* Identified several service-related subdomains including:

  * autodiscover.certifiedhacker.com
  * mail.certifiedhacker.com
  * webmail.certifiedhacker.com
  * ftp.certifiedhacker.com
  * cpanel.certifiedhacker.com
  * trustcenter.certifiedhacker.com
  * soc.certifiedhacker.com

## Evidence

Screenshots in this directory demonstrate module configuration, execution, discovered hosts, and dashboard statistics.

## Conclusion

Recon-ng successfully performed passive subdomain enumeration and infrastructure discovery using publicly available information without conducting intrusive scanning activities.
