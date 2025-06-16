---
date: 2025-06-16T15:51:28+02:00
title: Fattura Elettronica v4
tags: ["dotnet", "open-source", "fattura elettronica"]
---
I just released [FatturaElettronica.NET v4](https://www.nuget.org/packages/FatturaElettronica/4.0.0). The major version bump is due to a minor breaking change introduced with this version. 

After removing the BouncyCastle dependency ([v3.4.16](https://fatturaelettronicaopensource.org/docs/changelog.html#v-3416)) for signature, content extraction, and encoding purposes, a few minor behavioral changes were introduced in the library.

1. It was previously possible to extract content from documents with tampered signatures (if signature validation was flagged false)
2. Signature exceptions were being misreported as Base64 `FormatExceptions` for non-base64 input files

After a [lengthy analysis and troubleshooting](https://github.com/FatturaElettronica/FatturaElettronica.NET/issues/431), it was determined that System.Cryptography (which now replaces BouncyCastle) cannot support the successful decoding of tampered invoices. However, this is undesirable as a feature in the first place. The result is a breaking change: attempting to read tampered documents will now invariably throw `SignatureException`. 

Many thanks to Paolo Manili, aka Delta-38, for [contributing](https://github.com/FatturaElettronica/FatturaElettronica.NET/pull/434) this remarkable update.