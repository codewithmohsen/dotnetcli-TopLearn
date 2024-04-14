## Video 3 Helper - ساخت پروژه بک اند

note: Because of facing this error in bottom instrucanes:
```
~/aspdotnetcoreapi ❯ dotnet add Application reference Data 
```
```
Found a project `/.../Application/Application.csproj` but it is invalid.
```
```
~/aspdotnetcoreapi ❯ dotnet add IOC reference Application        
```
```
Found a project `/.../Application/Application.csproj` but it is invalid.
```
I found that just Application layer has has this error and i think it is about dotnet structure So  I reaname each layer with adding "Layer" at the end ofmy those names:
1. DataLayer instead of Data
2. DomainLayer instead of Domain
3. ApplicationLayer instead of Application
4. IOCLayer instead of IOC
5. PresentationLayer instead of Presentation 

### step1: Create Main Blank Soultion
in visual studio: Create an empty solution containing no projects.
in dotnet cli: Create new ASP.NET Core Empty project.
```
mkdir [project-name]
cd [project-name]
dotnet new web
```
### step2: Create subProjects
#### 1. Create "Domain" clsslibrary template solution.
```
mkdir DomainLayer
cd DomainLayer
dotnet new classlib
rm Class1.cs
```
or
```
cd ..
dotnet new classlib --output DomainLayer
cd DomainLayer
rm Class1.cs
```
#### 2. Create "Data" clsslibrary template solution.
```
cd ..
mkdir DataLayer
cd DataLayer
dotnet new classlib
rm Class1.cs
```
or
```
cd ..
dotnet new classlib --output DataLayer
cd DataLayer
rm Class1.cs
```
#### 3. Create "Application" clsslibrary template solution.
```
cd ..
mkdir ApplicationLayer
cd ApplicationLayer
dotnet new classlib
rm Class1.cs
```
or
```
cd ..
dotnet new classlib --output ApplicationLayer
cd ApplicationLayer
rm Class1.cs
```
#### 4. Create "IOC" clsslibrary template solution.
```
cd ..
mkdir IOCLayer
cd IOCLayer
dotnet new classlib
rm Class1.cs
```
or
```
cd ..
dotnet new classlib --output IOCLayer
cd IOCLayer
rm Class1.cs
```
#### 5. Create "Presentation" ASP.NET Core Web App (Model-View-Controller) template solution.
Because of the basic way needs complex customization so just try second way as bottom:
```
cd ..
dotnet new mvc --name app --output PresentationLayer
```

### Set Dependencies
Presentation > IOC > Application> Data > Domain
#### 1. DataLayer needs DomainLayer as referende
```
dotnet add DataLayer reference DomainLayer
```
or
```
cd DataLayer
dotnet add reference ../DomainLayer/DomainLayer.csproj
```
#### 2. DataLayer needs ApplicationLayer as referende
```
cd ..
dotnet add ApplicationLayer reference DataLayer
```
or
```
cd ApplicationLayer
dotnet add reference ../DataLayer/DataLayer.csproj
```
#### 3. IOCLayer needs ApplicationLayer as referende
```
cd ..
dotnet add IOCLayer reference ApplicationLayer
```
or
```
cd IOCLayer
dotnet add reference ../ApplicationLayer/ApplicationLayer.csproj
```
#### 4. PresentationLayer needs IOCLayer as referende
```
cd ..
dotnet add PresentationLayer reference IOCLayer
```
or
```
cd PresentationLayer
dotnet add reference ../IOCLayer/IOCLayer.csproj
```
### Create Subfolder
```
cd DomainLayer
mkdir Entities DTOs Interfaces
cd ..
cd DataLayer
mkdir Context Repositories
cd ..
cd ApplicationLayer
mkdir Services Extensions Senders
cd ..
cd Services
mkdir Interfaces Implementations
cd ..
cd ..
cd IOCLayer
mkdir Dipendencies
```
### Add sub projects to main solution
```
dotnet sln add DomainLayer/DomainLayer.csproj
dotnet sln add DataLayer/DataLayer.csproj
dotnet sln add ApplicationLayer/ApplicationLayer.csproj
dotnet sln add IOCLayer/IOCLayer.csproj
dotnet sln add dotnet sln add PresentationLayer/app.csproj 
```
now *.sln file updated.
```
dotnet sln list
Project(s)
----------
ApplicationLayer/ApplicationLayer.csproj
aspdotnetcoreapi.csproj
DataLayer/DataLayer.csproj
DomainLayer/DomainLayer.csproj
IOCLayer/IOCLayer.csproj
PresentationLayer/app.csproj
```
### download all nuget packages it refrences if you used clone other projects here
```
cd ..
dotnet restore
```
### build all projects once
```
cd PresentationLayer
dotnet build

MSBuild version 17.9.6+a4ecab324 for .NET
  Determining projects to restore...
  All projects are up-to-date for restore.
  DomainLayer -> /Users/mohsen/pre canada ASP Core API/aspdotnetcoreapi/DomainLayer/bin/Debug/net8.0/DomainLayer.dll
  DataLayer -> /Users/mohsen/pre canada ASP Core API/aspdotnetcoreapi/DataLayer/bin/Debug/net8.0/DataLayer.dll
  ApplicationLayer -> /Users/mohsen/pre canada ASP Core API/aspdotnetcoreapi/ApplicationLayer/bin/Debug/net8.0/ApplicationLayer.dll
  IOCLayer -> /Users/mohsen/pre canada ASP Core API/aspdotnetcoreapi/IOCLayer/bin/Debug/net8.0/IOCLayer.dll
  app -> /Users/mohsen/pre canada ASP Core API/aspdotnetcoreapi/PresentationLayer/bin/Debug/net8.0/app.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:01.39
```
