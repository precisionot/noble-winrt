# WinRT bindings for noble on windows.

## Forked from and based off of:
 https://github.com/fido-alliance/noble-winrt   
 https://github.com/Timeular/noble-winrt

## Changes and improvements
* Doesn't crash like `noble-uwp` when running for days.
* Fixed the service uuid filter used in scan start.
* Faster discovery when only requesting one service. Old versions of noble-winrt and noble-uwp would request all services over BLE and then cut down to one, instead of only requesting one in the first place.
* Fix the connectable flag to update on every adcertisement. Old versions would use the value from the first advert, and never update. 

## Todos
* Eliminate the local cache in this binding as windows has its own?
https://github.com/Timeular/noble-winrt/issues/24
* Be able to pass instant errors into noble. Currently this cant be done, and the user will just have to rely on timeouts.
https://github.com/abandonware/noble/issues/135


<br><br><br>
# Original readme:

_This is a rewrite of [noble-uwp](https://github.com/jasongin/noble-uwp) using the [C++/WinRT](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) API._

## System Requirements
 * Node.js v6.14.2 or later.
 * Windows 10 build 10.0.15063 or later
 * Windows 10 SDK build 10.0.17134.0

## Usage
Simply require `noble-winrt` instead of `noble`:
```javascript
const noble = require('noble-winrt');
```
On non-Windows platforms or Windows versions lower than 10.0.15063 this will use the regular [noble](https://github.com/sandeepmistry/noble/blob/master/README.md) implementation and on Windows version 10.0.15063 or later it will use the native binding using the C++/WinRT API.

## Implementation Status
Everything should work that also works with the regular noble bindings except:
 * Writing/Reading to descriptor handles is not supported
 * Broadcast is not supported