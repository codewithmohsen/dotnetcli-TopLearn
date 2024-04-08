## Video 04 Helper

### install Microsoft.EntityFrameworkCore
```
cd DataLayer
dotnet tool search microsoft.entityframeworkcore
dotnet add package dotnet-ef
```
bug: Package dotnet-ef 8.0.3 is not compatible with net8.0
debug:
```
dotnet tool install -g dotnet-ef --version 7
```
note: Tool 'dotnet-ef' was reinstalled with the stable version (version '7').
