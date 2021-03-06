[![Build Status](https://travis-ci.org/miekg/dns.svg?branch=master)](https://travis-ci.org/miekg/dns)

# Alternative (more granular) approach to a DNS library

> Less is more.

Complete and usable DNS library. All widely used Resource Records are
supported, including the DNSSEC types. It follows a lean and mean philosophy.
If there is stuff you should know as a DNS programmer there isn't a convenience
function for it. Server side and client side programming is supported, i.e. you
can build servers and resolvers with it.

If you like this, you may also be interested in:

* https://github.com/miekg/unbound -- Go wrapper for the Unbound resolver.

# Goals

* KISS;
* Fast;
* Small API, if its easy to code in Go, don't make a function for it.

# Users

A not-so-up-to-date-list-that-may-be-actually-current:

* https://github.com/abh/geodns
* http://www.statdns.com/
* http://www.dnsinspect.com/
* https://github.com/chuangbo/jianbing-dictionary-dns
* http://www.dns-lg.com/
* https://github.com/fcambus/rrda
* https://github.com/kenshinx/godns
* https://github.com/skynetservices/skydns
* https://github.com/DevelopersPL/godnsagent
* https://github.com/duedil-ltd/discodns

Send pull request if you want to be listed here.

# Features

* UDP/TCP queries, IPv4 and IPv6;
* RFC 1035 zone file parsing ($INCLUDE, $ORIGIN, $TTL and $GENERATE (for all record types) are supported;
* Fast:
    * Reply speed around ~ 80K qps (faster hardware results in more qps);
    * Parsing RRs ~ 100K RR/s, that's 5M records in about 50 seconds;
* Server side programming (mimicking the net/http package);
* Client side programming;
* DNSSEC: signing, validating and key generation for DSA, RSA and ECDSA;
* EDNS0, NSID;
* AXFR/IXFR;
* TSIG, SIG(0);
* DNS name compression;
* Depends only on the standard library.

Have fun!

Miek Gieben  -  2010-2012  -  <miek@miek.nl>

# Building

Building is done with the `go` tool. If you have setup your GOPATH
correctly, the following should work:

    go get github.com/miekg/dns
    go build github.com/miekg/dns

## Examples

A short "how to use the API" is at the beginning of dns.go (this also will show
when you call `godoc github.com/miekg/dns`).

Example programs can be found in the `github.com/miekg/exdns` repository.

## Supported RFCs

*all of them*

* 103{4,5} - DNS standard
* 1348 - NSAP record
* 1982 - Serial Arithmetic
* 1876 - LOC record
* 1995 - IXFR
* 1996 - DNS notify
* 2136 - DNS Update (dynamic updates)
* 2181 - RRset definition - there is no RRset type though, just []RR
* 2537 - RSAMD5 DNS keys
* 2065 - DNSSEC (updated in later RFCs)
* 2671 - EDNS record
* 2782 - SRV record
* 2845 - TSIG record
* 2915 - NAPTR record
* 2929 - DNS IANA Considerations
* 3110 - RSASHA1 DNS keys
* 3225 - DO bit (DNSSEC OK)
* 340{1,2,3} - NAPTR record
* 3445 - Limiting the scope of (DNS)KEY
* 3597 - Unkown RRs
* 403{3,4,5} - DNSSEC + validation functions
* 4255 - SSHFP record
* 4343 - Case insensitivity
* 4408 - SPF record
* 4509 - SHA256 Hash in DS
* 4592 - Wildcards in the DNS
* 4635 - HMAC SHA TSIG
* 4701 - DHCID
* 4892 - id.server
* 5001 - NSID
* 5155 - NSEC3 record
* 5205 - HIP record
* 5702 - SHA2 in the DNS
* 5936 - AXFR
* 5966 - TCP implementation recommendations
* 6605 - ECDSA
* 6725 - IANA Registry Update
* 6742 - ILNP DNS
* 6891 - EDNS0 update
* 6895 - DNS IANA considerations
* 6975 - Algorithm Understanding in DNSSEC
* 7043 - EUI48/EUI64 records
* 7314 - DNS (EDNS) EXPIRE Option
* xxxx - URI record (draft)
* xxxx - EDNS0 DNS Update Lease (draft)

## Loosely based upon

* `ldns`
* `NSD`
* `Net::DNS`
* `GRONG`

## TODO

* privatekey.Precompute() when signing?
* Last remaining RRs: APL, ATMA, A6 and NXT;
* Missing in parsing: ISDN, UNSPEC, ATMA;
* CAA parsing is broken;
* NSEC(3) cover/match/closest enclose;
* Replies with TC bit are not parsed to the end;
* Create IsMsg to validate a message before fully parsing it.
