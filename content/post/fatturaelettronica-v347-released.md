---
date: 2023-04-05T07:05:25+01:00
title: "FatturaElettronica for .NET v3.4.7"
share: false
tags: ["dotnet", "open-source", "fattura-elettronica"]
---
Fattura Elettronica for .NET v3.4.7 was [released][1] on NuGet today. The [Fattura Elettronica project][2] allows for
the validation and de/serialization of electronic invoices adhering to the canon defined by the Italian Revenue Agency.

This release refines how the one-cent tolerance is accounted for in validation checks of types 00421 and 00423. As is
often the case, there are subtle differences between the theoretical implementation defined in the official specs and
the actual validation implemented by the same Agency that released said specs. See the [relevant ticket][3] for the
details.

