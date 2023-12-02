---
title: TLS 1.3 support
description: This article discusses TLS 1.3 support with SQL Server 2022.
author: srdan-bozovic-msft
ms.author: srbozovi
ms.date: 11/16/2023
ms.service: sql
ms.subservice: security
ms.topic: conceptual
monikerRange: ">=sql-server-ver16 || >=sql-server-linux-ver16"
---
# TLS 1.3 support

[!INCLUDE [SQL Server 2022](../../../includes/applies-to-version/sqlserver2022.md)]

Beginning with [!INCLUDE [sssql22-md](../../../includes/sssql22-md.md)], [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] supports Transport Layer Security (TLS) 1.3 when TDS 8.0 is used.

[!INCLUDE [sssql19-md](../../../includes/sssql19-md.md)] and earlier versions don't support TLS 1.3.

## Differences between TLS 1.2 and TLS 1.3

TLS 1.3 reduces the number of round trips from two to one during the handshake phase, making it faster and more secure than TLS 1.2. The server hello packet containing server certificate is encrypted and one Round Trip Time (1-RTT) resumption is discontinued, and replaced with 0-RTT resumption based on client key share. Added security of TLS 1.3 comes from discontinuing certain cyphers and algorithms.

Here's a list of algorithms and ciphers removed in TLS 1.3:

- RC4 stream cipher
- RSA key exchange
- SHA-1 hash function
- CBC (block) mode ciphers
- MD5 algorithm
- Various non-ephemeral Diffie-Hellman groups
- EXPORT-strength ciphers
- DES
- 3DES
## Note: Do not disable TLS 1.2 protocol while implementing TLS 1.3 as it is still required to start SQL service at the moment.
## Related content

- [Connect to SQL Server with strict encryption](connect-with-strict-encryption.md)
