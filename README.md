# Documentation for Mail Transfer Protocols

| MTP (Draft) | MTP | SMTP | SMTP | (E)SMTP | (E)SMTP |
| - | - | - | - | - | - |
| RFC 772 | RFC 780 | RFC 788 | RFC 821 | RFC 2821 | RFC 5321 |
| | `ABRT` |
| | `CONT` |
| | | `DATA` | `DATA` | `DATA` | `DATA` |
| | | | | `"EHLO" SP Domain` | `"EHLO" SP ( Domain / address-literal )` |
| | | `EXPN <SP> <string>` | `EXPN <SP> <string>` | `"EXPN" SP String` | `"EXPN" SP String` |
| | | `HELO <SP> <host>` | `HELO <SP> <domain>` | `"HELO" SP Domain` | `"HELO" SP Domain` |
| `HELP [<SP> <string>]` | `HELP [<SP> <string>]` | `HELP [<SP> <string>]` | `HELP [<SP> <string>]` | `"HELP" [ SP String ]` | `"HELP" [ SP String ]` |
| `MAIL <SP> FROM:<sender> [<SP> TO:<path>]` | `MAIL <SP> FROM:<sender-path> [<SP> TO:<receiver-path>]` | `MAIL <SP> FROM:<reverse-path>` | `MAIL <SP> FROM:<reverse-path>` | `MAIL FROM:<reverse-path> [SP <mail-parameters> ]` | `"MAIL FROM:" Reverse-path [SP Mail-parameters]`
| `MRCP <SP> TO:<path>` | `MRCP <SP> TO:<receiver-path>` |
| `MRSQ [<SP> <scheme>]` | `MRSQ [<SP> <scheme>]` |
| `NOOP` | `NOOP` | `NOOP` | `NOOP` | `"NOOP" [ SP String ]` | `"NOOP" [ SP String ]` |
| `QUIT` | `QUIT` | `QUIT` | `QUIT` | `QUIT` | `QUIT` |
| | | `RCPT <SP> TO:<forward-path>` | `RCPT <SP> TO:<forward-path>` | `RCPT TO:<forward-path> [ SP <rcpt-parameters> ]` | `"RCPT TO:" ( "<Postmaster@" Domain ">" / "<Postmaster>" / Forward-path ) [SP Rcpt-parameters]`
| | | `RSET` | `RSET` | `RSET` | `RSET` |
| | | `SAML <SP> FROM:<reverse-path>` | `SAML <SP> FROM:<reverse-path>` |
| | | `SEND <SP> FROM:<reverse-path>` | `SEND <SP> FROM:<reverse-path>` |
| | | `SOML <SP> FROM:<reverse-path>` | `SOML <SP> FROM:<reverse-path>` |
| | | | `TURN` |
| | | `VRFY <SP> <string>` | `VRFY <SP> <string>` | `"VRFY" SP String` | `"VRFY" SP String` |
