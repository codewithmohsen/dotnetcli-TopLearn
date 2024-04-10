## Note1: Change dotnet sdk version
### Check your current sdk version
```
dotnet --version
8.0.203
```
### Download new sdk version
Goto https://dotnet.microsoft.com/en-us/download/dotnet and download version 7!
### Check all installed sdk versions
```
dotnet --list-sdks
7.0.407 [/usr/local/share/dotnet/sdk]
8.0.203 [/usr/local/share/dotnet/sdk]
```
### Set your project's sdk version
Go to root of your project and run to create global.json file.
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
now
```
dotnet --version     
7.0.407
```
### Update your project
and in all *.csproj files update this line
```
</Project>
  .
  .
  .
  <PropertyGroup>
    <TargetFramework>net7.0</TargetFramework>
    .
    .
    .
  </PropertyGroup>
  .
  .
  .
</Project>
```
Done :)
