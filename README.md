# Portalum.Zvt.EasyPay

If you are looking for a simple way to automatically transfer the amount to be paid to your payment terminal, then you have come to the right place. EasyPay allows you to start a payment at the payment terminal with the passing of the amount. It is important that your payment terminal supports the ZVT protocol.

![Portalum.Zvt.EasyPay](/doc/EasyPay.png)

```bash
Portalum.Zvt.EasyPay.exe --amount 1.23
```

## Installing and running EasyPay

**To use the tool, the following steps must be performed**

- Install [.NET Desktop Runtime 6.x](https://dotnet.microsoft.com/download/dotnet/6.0)
- Download and extract the EasyPay ([download](https://github.com/Portalum/Portalum.Zvt.EasyPay/releases/latest/download/Portalum.Zvt.EasyPay.zip))

## Configuration

The configuration of the payment terminal `IpAddress` and the `Port` must be set in the `appsettings.json`.
```json
{
  "IpAddress": "192.168.100.20",
  "Port": 20007
}
```

## ReturnCodes
It can be easily checked via the ReturnCode whether the payment process was successful.

ReturnCode | Status | Description | 
--- | --- | --- |
0 | Successful | Payment successful |
-1 | Error | Payment not successful |
-2 | Error | Command line parameter invalid |
-3 | Error | Configuration file not available |
-4 | Error | Cannot connect |
-5 | Error | Application close by user |

## Troubleshooting
A log file is automatically created with all important information about the payment process.<br>
You find all log lines in the `default-yyyyMMdd.log` file.

## Examples

### Start payment

#### java
```java
var processBuilder = new ProcessBuilder();
processBuilder.command("Portalum.Zvt.EasyPay.exe", "--amount", "1.23");
var process = processBuilder.start();
var returnCode = process.waitFor();
```

#### powershell
```ps
$process = Start-Process Portalum.Zvt.EasyPay.exe -WindowStyle Hidden -ArgumentList "--amount 1.23" -PassThru -Wait
$process.ExitCode
```

#### windows cmd
```cmd
start /w Portalum.Zvt.EasyPay.exe --amount 1.23
echo %errorlevel%
```
