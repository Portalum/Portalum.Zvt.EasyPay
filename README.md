# Portalum.Zvt.EasyPay

<img src="https://raw.githubusercontent.com/Portalum/Portalum.Zvt/main/doc/logo.png" width="150" title="Portalum Zvt EasyPay" alt="Portalum Zvt EasyPay" align="left">

Portalum.Zvt.EasyPay allows to start a payment at the payment terminal with the passing of the amount

## EasyPay
EasyPay allows to start a payment at the payment terminal with the passing of the amount

![Portalum.Zvt.EasyPay](/doc/EasyPay.png)

```bash
Portalum.Zvt.EasyPay.exe --amount 1.23
```

The configuration of the payment terminal `IpAddress` and the `Port` must be set in the `appsettings.json`. A log file is created automatically.

**ReturnCodes**
ReturnCode | Status | Description | 
--- | --- | --- |
0 | Successful | Payment successful |
-1 | Error | Payment not successful |
-2 | Error | Command line parameter invalid |
-3 | Error | Configuration file not available |
-4 | Error | Cannot connect |