# Portalum.Zvt.EasyPay

EasyPay allows you to start a payment at the payment terminal with the passing of the amount.<br>
A log file is automatically created with all important information about the payment process `default-yyyyMMdd.log`.

![Portalum.Zvt.EasyPay](/doc/EasyPay.png)

```bash
Portalum.Zvt.EasyPay.exe --amount 1.23
```

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

## Examples

### Start payment

**java**
```java
var processBuilder = new ProcessBuilder();
processBuilder.command("Portalum.Zvt.EasyPay.exe", "--amount", "1.23");
var process = processBuilder.start();
var returnCode = process.waitFor();
```

**powershell**
```ps
$process = Start-Process Portalum.Zvt.EasyPay.exe -WindowStyle Hidden -ArgumentList "--amount 1.23" -PassThru -Wait
$process.ExitCode
```

**windows cmd**
```cmd
start /w Portalum.Zvt.EasyPay.exe --amount 1.23
echo %errorlevel%
```
