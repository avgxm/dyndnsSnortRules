## Synopsis

Generate Snort rules from a list of dns domains found in http://www.malware-domains.com/files/dynamic_dns.zip

## Example
```
$ ./dyndnsSnortRules.py 
$ head local.rules 
#autogenerated on 2015-09-02T14:47:40.178848Z
alert udp $HOME_NET any -> $DNS_SERVERS 53 (msg:"DNS Query for a dynamic domain 0000000000000000000000.com"; content:"|01 00 00 01 00 00 00 00 00 00|"; depth:10; offset:2; content:"|16|0000000000000000000000|03|com|00|"; fast_pattern; nocase; distance:0; classtype:bad-unknown; sid:1000000; rev:1;)
alert udp $HOME_NET any -> $DNS_SERVERS 53 (msg:"DNS Query for a dynamic domain 020huahai.com"; content:"|01 00 00 01 00 00 00 00 00 00|"; depth:10; offset:2; content:"|09|020huahai|03|com|00|"; fast_pattern; nocase; distance:0; classtype:bad-unknown; sid:1000001; rev:1;)
alert udp $HOME_NET any -> $DNS_SERVERS 53 (msg:"DNS Query for a dynamic domain 021christine.com"; content:"|01 00 00 01 00 00 00 00 00 00|"; depth:10; offset:2; content:"|0c|021christine|03|com|00|"; fast_pattern; nocase; distance:0; classtype:bad-unknown; sid:1000002; rev:1;)
$
