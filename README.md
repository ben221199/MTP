# Documentation for Mail Transfer Protocols

| Protocol | Cleartext Port | STARTTLS Port | SSL/TLS Port |
| - | - | - | - |
| MTP | `57` | *STARTTLS not supported* | *Not defined* |
| SMTP | `25` | *STARTTLS not supported, see ESMTP* | *Not defined* |
| ESMTP | `25` | `25` | *Not defined* |
| (E)SMTP Submission | `587` | `587` | `465` |
| LMTP | `24` (not defined, but commonly used) | `24` (not defined, but commonly used) | *Not defined* |

## RFCs for (E)SMTP and LMTP

| RFC 772 / MTP (Draft) | RFC 780 / MTP | RFC 788 / SMTP | RFC 821 / SMTP | RFC 2033 / LMTP | RFC 2821 / (E)SMTP | RFC 5321 / (E)SMTP |
| - | - | - | - | - | - | - |
| | `ABRT` |
| | `CONT` |
| | | `DATA` | `DATA` | `DATA` | `DATA` | `DATA` |
| | | *Extendable (using RFC 1425, RFC 1651, RFC 1869)* | *Extendable (using RFC 1425, RFC 1651, RFC 1869)* | *See LHLO* | `"EHLO" SP Domain` | `"EHLO" SP ( Domain / address-literal )` |
| | | `EXPN <SP> <string>` | `EXPN <SP> <string>` | <-- | `"EXPN" SP String` | `"EXPN" SP String` |
| | | `HELO <SP> <host>` | `HELO <SP> <domain>` | *See LHLO* | `"HELO" SP Domain` | `"HELO" SP Domain` |
| `HELP [<SP> <string>]` | `HELP [<SP> <string>]` | `HELP [<SP> <string>]` | `HELP [<SP> <string>]` | <-- | `"HELP" [ SP String ]` | `"HELP" [ SP String ]` |
| | | | | `LHLO` |
| `MAIL <SP> FROM:<sender> [<SP> TO:<path>]` | `MAIL <SP> FROM:<sender-path> [<SP> TO:<receiver-path>]` | `MAIL <SP> FROM:<reverse-path>` | `MAIL <SP> FROM:<reverse-path>` | <-- | `MAIL FROM:<reverse-path> [SP <mail-parameters> ]` | `"MAIL FROM:" Reverse-path [SP Mail-parameters]`
| `MRCP <SP> TO:<path>` | `MRCP <SP> TO:<receiver-path>` |
| `MRSQ [<SP> <scheme>]` | `MRSQ [<SP> <scheme>]` |
| `NOOP` | `NOOP` | `NOOP` | `NOOP` | <-- | `"NOOP" [ SP String ]` | `"NOOP" [ SP String ]` |
| `QUIT` | `QUIT` | `QUIT` | `QUIT` | <-- | `QUIT` | `QUIT` |
| | | `RCPT <SP> TO:<forward-path>` | `RCPT <SP> TO:<forward-path>` | <-- | `RCPT TO:<forward-path> [ SP <rcpt-parameters> ]` | `"RCPT TO:" ( "<Postmaster@" Domain ">" / "<Postmaster>" / Forward-path ) [SP Rcpt-parameters]`
| | | `RSET` | `RSET` | <-- | `RSET` | `RSET` |
| | | `SAML <SP> FROM:<reverse-path>` | `SAML <SP> FROM:<reverse-path>` | <-- | *Obsolete* | *Obsolete* |
| | | `SEND <SP> FROM:<reverse-path>` | `SEND <SP> FROM:<reverse-path>` | <-- | *Obsolete* | *Obsolete* |
| | | `SOML <SP> FROM:<reverse-path>` | `SOML <SP> FROM:<reverse-path>` | <-- | *Obsolete* | *Obsolete* |
| | | | `TURN` | <-- | *Deprecated* | *Deprecated* |
| | | `VRFY <SP> <string>` | `VRFY <SP> <string>` | <-- | `"VRFY" SP String` | `"VRFY" SP String` |

## RFCs for SMTP Service Extensions

| RFC 1425 | RFC 1651 | RFC 1869 |
| - | - | - |
| `"EHLO" SP domain` | `"EHLO" SP domain` | `"EHLO" SP domain` |

*Note: These RFCs are obsoleted since RFC 2821, because that RFC included the EHLO command.*

## ELHO/LHLO Keywords for (E)SMTP and LMTP

| Keyword | First defined in RFC | Updated by RFC | Deprecated/Obsoleted in RFC |
| - | - | - | - |
| `EXPN` | RFC821 | RFC5321 | - |
| `HELP` | RFC821 | RFC5321 | - |
| `SAML` | RFC821 | RFC1123 | RFC2821 |
| `SEND` | RFC821 | RFC1123 | RFC2821 |
| `SOML` | RFC821 | RFC1123 | RFC2821| 
| `TURN` | RFC821 | - | RFC2821 |

*Note: These (E)SMTP/LMTP commands are optional to implement. Ttheir EHLO/LHLO keyword should be listed if (still) implemented.*

# ELHO/LHLO Keywords for SMTP Service Extensions

| Keyword | RFC | Additional information |
| - | - | - |
| `8BITMIME` | RFC6152 | |
| `ATRN` | RFC2645 | No submission |
| `AUTH` |RFC4954 | |
| `BINARYMIME` | RFC3030 | |
| `BURL` | RFC4468 | Only submission |
| `CHECKPOINT` | RFC1845 | |
| `CHUNKING` | RFC3030 | |
| `CONNEG` | RFC4141 | |
| `CONPERM` | RFC4141 | |
| `DELIVERBY` | RFC2852 | |
| `DSN` | RFC3461 | |
| `ENHANCEDSTATUSCODES` | RFC2034 | |
| `ETRN` | RFC1985 | No submission |
| `FUTURERELEASE` | RFC4865 | |
| `LIMITS` | `draft-freed-smtp-limits` | Not yet a RFC |
| `MT-PRIORITY` | RFC6710 | |
| `MTRK` | RFC3885 | |
| `NO-SOLICITING` | RFC3865 | |
| `ONEX` | - | |
| `PIPELINING` | RFC2920 | |
| `REQUIRETLS` | RFC8689 | |
| `RRVS` | RFC7293 | |
| `SIZE` | RFC1870 | Also see `LIMITS`. |
| `SMTPUTF8` | RFC6531 | |
| `STARTTLS` | RFC3207 | |
| `SUBMITTER` | RFC4405 | Deprecated |
| `UTF8SMTP` | RFC5336 | Experimental: Deprecated by `SMTPUTF8`. |
| `VERB` | - | |

*Note: Not all keywords do mean that there also new commands. Some keywords indicate command parameters or support for some charset.*
