## Video 04 Helper

### install Microsoft.EntityFrameworkCore
```
cd DataLayer
dotnet tool search microsoft.entityframeworkcore
dotnet add package dotnet-ef
```
bug: Package dotnet-ef 8.0.3 is not compatible with net8.0
first check your .net version
```
dotnet --version
8.0.203                                            х HUP
```
Goto https://dotnet.microsoft.com/en-us/download/dotnet and download version 7! Then:
```
dotnet --list-sdks
7.0.407 [/usr/local/share/dotnet/sdk]
8.0.203 [/usr/local/share/dotnet/sdk]
```
```
dotnet new globaljson
```
open global.json and replace
```
{
  "sdk": {
    "version": "8.0.203"
  }
}
```
to
```
{
  "sdk": {
    "version": "7.0.407"
  }
}
```
```
dotnet tool install -g dotnet-ef --version 7
```
note: Tool 'dotnet-ef' was reinstalled with the stable version (version '7').
