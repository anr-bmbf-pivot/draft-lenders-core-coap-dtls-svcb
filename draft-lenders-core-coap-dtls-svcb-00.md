---
title: "Service Binding and Parameter Specification for CoAP over (D)TLS "
abbrev: "CoRE SVCB"
category: std

docname: draft-lenders-core-coap-dtls-svcb-00
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
area: "Web and Internet Transport"
workgroup: "Constrained RESTful Environments"
keyword:
 - CoRE
 - CoAP
 - SVCB
 - DTLS
venue:
  group: "Constrained RESTful Environments"
  type: "Working Group"
  mail: "core@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/core/"
  github: "anr-bmbf-pivot/draft-lenders-core-coap-dtls-svcb"
  latest: "https://anr-bmbf-pivot.github.io/draft-lenders-core-coap-dtls-svcb/draft-lenders-core-coap-dtls-svcb.html"

author:
 -  fullname: Martine Sophie Lenders
    org: TUD Dresden University of Technology
    abbrev: TU Dresden
    street: Helmholtzstr. 10
    city: Dresden
    code: D-01069
    country: Germany
    email: martine.lenders@tu-dresden.de
 -  name: Christian Amsüss
    email: christian@amsuess.com
 -  fullname: Thomas C. Schmidt
    organization: HAW Hamburg
    street: Berliner Tor 7
    city: Hamburg
    code: D-20099
    country: Germany
    email: t.schmidt@haw-hamburg.de
 -  name: Matthias Wählisch
    org: TUD Dresden University of Technology & Barkhausen Institut
    abbrev: TU Dresden & Barkhausen Institut
    street: Helmholtzstr. 10
    city: Dresden
    code: D-01069
    country: Germany
    email: m.waehlisch@tu-dresden.de

normative:
  RFC7252: coap
  RFC7301: alpn
  RFC9460: svcb
  RFC9463: dnr

informative:
  RFC8323: coap-tcp
  I-D.ietf-core-dns-over-coap: doc

--- abstract

This document specifies the usage of Service Parameters as used in SVCB ("Service Binding") DNS resource
records for the discovery of transport-layer-secured CoAP services.

--- middle

# Introduction

{{-svcb}} specifies the "SVCB" ("Service Binding") DNS resource records for looking up
communication endpoints of a service. Service Parameters (SvcParams) are used to
carry that information.
This document specifies which information from SvcParams can be used with CoAP services that are
secured by transport security, namely TLS and DTLS.
As an example, this information can be obtained as part of the discovery of DNS over CoAP (DoC) servers (see
{{-doc}}) that deploy TLS or DTLS to secure their messages.

# Terminology

SvcParams denotes the field in either DNS SVCB/HTTPS records as defined in {{-svcb}}, or DHCP and RA
messages as defined in {{-dnr}}.

{::boilerplate bcp14-tagged}

# Application-Layer Protocol Negotiation (ALPN) IDs

{{-svcb}} defines the "alpn" key, which is used to identify the service binding to a protocol suite
using its Application-Layer Protocol Negotiation (ALPN) ID {{-alpn}}.
For CoAP over TLS an ALPN ID was defined in {{-coap-tcp}}.
As it is not advisable to re-use the same ALPN ID for a different transport layer, an ALPN for
CoAP over DTLS is also registered in {{iana}}.
To discover CoAP services that secure their messages with TLS or DTLS, these ALPN IDs can be used in
the same manner as for any other service secured with transport layer security, as
described in {{-svcb}}.
Other authentication mechanisms are currently out of scope.

# Security Considerations

Any security considerations on SVCB resource records (see {{-svcb}}), also apply to this document.

# IANA Considerations {#iana}

## TLS ALPN for CoAP

The following entry has been added to the
"TLS Application-Layer Protocol Negotiation (ALPN) Protocol IDs" registry,
which is part of the "Transport Layer Security (TLS) Extensions" group.

* Protocol: CoAP (over DTLS)
* Identification sequence: 0x63 0x6f ("co")
* Reference: {{-coap}} and \[this document\]

Note that {{-coap}} does not define the use of the ALPN TLS extension during connection the DTLS handshake.
This document does not change that, and thus does not establish any rules like those in {{Section 8.2 of -coap-tcp}}.


--- back

# Change Log


# Acknowledgments
{:numbered="false"}

TODO acknowledge.
