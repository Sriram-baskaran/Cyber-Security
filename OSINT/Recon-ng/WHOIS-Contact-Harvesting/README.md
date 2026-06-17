# Recon-ng: WHOIS Contact Harvesting

## Objective

Perform passive reconnaissance to collect publicly available Whois Point-of-Contact (POC) information associated with a target domain.

## Target

facebook.com

## Module Used

recon/domains-contacts/whois_pocs

## Commands Used

```bash
modules load recon/domains-contacts/whois_pocs
options set SOURCE facebook.com
options list
run
show contacts
dashboard
```

## Methodology

1. Loaded the Whois POC Harvester module in Recon-ng.
2. Configured `facebook.com` as the target domain.
3. Queried ARIN Whois REST services.
4. Retrieved publicly available Point-of-Contact information.
5. Stored the results in Recon-ng's contacts database.

## Findings

The module successfully identified two publicly available Whois contacts:

* Brandon Stout

  * Email: [bstout@facebook.com](mailto:bstout@facebook.com)
  * Region: Chicago, IL
  * Country: United States

* Operations

  * Email: [domain@facebook.com](mailto:domain@facebook.com)
  * Region: Menlo Park, CA
  * Country: United States

## Evidence

Screenshots in this directory demonstrate module configuration, execution, contact discovery, and dashboard statistics.

## Conclusion

Recon-ng successfully harvested publicly available Whois contact information using passive OSINT techniques without performing intrusive scanning or exploitation activities.

## Disclaimer

The information collected in this exercise was obtained entirely from publicly available Whois records and was gathered solely for educational and defensive security learning purposes.
