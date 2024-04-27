# `dig`

## Description:
`dig` (domain information groper) is a command-line utility used for querying DNS (Domain Name System) servers. It provides detailed information about DNS records, including A, AAAA, CNAME, MX, NS, PTR, SOA, SRV, and TXT records.

## Syntax:
`dig [options] [name] [type]`

## Options:
- `@server`: Specify the DNS server to query. This can be an IP address or a domain name.
- `-x`: Perform a reverse DNS lookup (PTR query) based on an IP address.
- `+trace`: Enable tracing of the DNS query resolution process.
- `+short`: Display only the essential information in a concise format.
- `+identify`: Display the IP address and port number of the server that responded to the query.
- `+noquestion`: Suppress the display of the question section of the query.
- `+nocomments`: Suppress the display of comment lines in the output.
- `+noauthority`: Suppress the display of authority section of the response.
- `+noadditional`: Suppress the display of additional section of the response.
- `+noanswer`: Suppress the display of answer section of the response.
- `+multiline`: Print records in a multiline format for better readability.
- `+onesoa`: Display only one SOA record when performing zone transfers.
- `+retry`: Set the number of retries for UDP queries.
- `+time`: Set the timeout for DNS queries in seconds.
- `+bufsize`: Set the maximum UDP packet size for DNS queries.
- `+tcp`: Use TCP instead of UDP for DNS queries.
- `+noignore`: Do not ignore truncation errors.
- `+ignore`: Ignore truncation errors.
- `+besteffort`: Try to display the answer even in case of errors.
- `+noquestion`: Suppress the display of the question section of the query.
- `+noadditional`: Suppress the display of additional section of the response.

