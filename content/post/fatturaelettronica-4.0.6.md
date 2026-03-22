---
date: 2026-03-22T09:05:32+01:00
title: Fattura Elettronica 4.0.6
tags: ["open source", "dotnet", "fattura elettronica"]
---
A couple of days ago I released [FatturaElettronica 4.0.6](https://www.nuget.org/packages/FatturaElettronica/4.0.6). It adds support for legacy `windows-1252` encoding to both XML and P7M invoices, a long-standing annoyance that could previously be circumvented via external code.

`windows-1252` encoding in Italian e-invoices has been a persistent headache — it's technically outside the FatturaPA spec (which mandates UTF-8), but it crops up often enough in real-world invoices from older or misconfigured billing systems that users kept running into it. The [Invoicetronic](https://invoicetronic.com) stack has been updated accordingly.