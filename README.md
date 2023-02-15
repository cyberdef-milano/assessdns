# ~$ assessdns

`assessdns` is a shell script (legacy version of @5amu 's tool `dnshunter`) which checks for multiple and typical nameservers' misconfigurations.

To contextualize this tool here's the author blog post about the topics: [https://www.casalinovalerio.com/p/bgp-hijacking/](https://www.casalinovalerio.com/p/bgp-hijacking/).


## Checks

* "soa_info": will check the vailidy and conformation to international standards of the SOA record 
* "zone_transfer": will check wether the nameserver would transfer its zone and leak all records
* "any_query": will check if the nameserver answers to ANY queries, making it potentially vulnerable to an amplification attack
* "glue_record": will check if the nameserver has glue records for other nameservers responsible for the zone as well as itself
* "dnssec": will check if the nameserver implements DNSSEC
* "spf": will check the safety of the SPF record
* "dmarc": will check the safety of the DMARC record
* "dkim": will attempt to locate the DKIM record for the provided domain
* "geo": will check wether the various nameservers are correctly distributed geographically  


## Usage

```
Usage: ./assessdns [-h] [-v] [-n <file>] -d DOMAIN

    -h|--help          Display help and exit
    -v|--verbose       Show verbose output
    -d|--domain        Specify target domain
    -n|--file-ns       File with nameservers (new-line separated)
```