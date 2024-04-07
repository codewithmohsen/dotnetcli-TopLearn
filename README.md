# dotnetcli-TopLearn
CLI helper to TopLearn course https://toplearn.com/c/5906

## Video 3 Helper
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
mkdir Domain
cd Domain
dotnet new classlib
rm Class1.cs
```
or
```
cd ..
dotnet new classlib --output Domain
cd Domain
rm Class1.cs
```
#### 2. Create "Data" clsslibrary template solution.
```
cd ..
mkdir Data
cd Data
dotnet new classlib
rm Class1.cs
```
or
```
cd ..
dotnet new classlib --output Data
cd Data
rm Class1.cs
```
#### 3. Create "Application" clsslibrary template solution.
```
cd ..
mkdir Application
cd Application
dotnet new classlib
rm Class1.cs
```
or
```
cd ..
dotnet new classlib --output Application
cd Application
rm Class1.cs
```
#### 4. Create "IOC" clsslibrary template solution.
```
cd ..
mkdir IOC
cd IOC
dotnet new classlib
rm Class1.cs
```
or
```
cd ..
dotnet new classlib --output IOC
cd IOC
rm Class1.cs
```
#### 5. Create "Presentation" ASP.NET Core Web App (Model-View-Controller) template solution.
Because of the basic way needs complex customization so just try second way as bottom:
```
cd ..
dotnet new mvc --name app --output Presentation
```

### Set Dependencies
Presentation > IOC > Application > Data > Domain 
- [x] ```dotnet add Data reference Domain``` 
- [ ] ```dotnet add Application reference Data```
error: Found a project `/Users/mohsen/personal-projects/aspdotnetcoreapi/Application/Application.csproj` but it is invalid.
- [ ] ```dotnet add IOC reference Application```
error: Found a project `/Users/mohsen/personal-projects/aspdotnetcoreapi/Application/Application.csproj` but it is invalid.
- [x] ```dotnet add Presentation reference IOC```

