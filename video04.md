## Video 04 Helper


### in DataLayer
```
cd DataLayer
```
#### 1. install Microsoft.EntityFrameworkCore package
Visit https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/ to know installation cli.
```
dotnet add package Microsoft.EntityFrameworkCore
```
now /DataLayer/project.assets.json file is updated
#### 2. install Microsoft.EntityFrameworkCore.Design package
Visit https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.Design/ to know installation cli.
```
dotnet add package Microsoft.EntityFrameworkCore.Design
```
#### 3. install Microsoft.EntityFrameworkCore.Tools package
Visit https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.Tools/ to know installation cli.
```
dotnet add package Microsoft.EntityFrameworkCore.Tools
```
#### 4. install Microsoft.EntityFrameworkCore.SqlServer package
Visit https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.sqlserver/ to know installation cli.
```
dotnet add package Microsoft.EntityFrameworkCore.SqlServer 
```
now check installed package in current folder
```
dotnet list package
Project 'DataLayer' has the following package references
   [net8.0]: 
   Top-level Package                              Requested   Resolved
   > Microsoft.EntityFrameworkCore                8.0.3       8.0.3   
   > Microsoft.EntityFrameworkCore.Design         8.0.3       8.0.3   
   > Microsoft.EntityFrameworkCore.SqlServer      8.0.3       8.0.3   
   > Microsoft.EntityFrameworkCore.Tools          8.0.3       8.0.3
```
### in DataLayer/Context
```
cd context
dotnet new class --name appDBContext
```
update DataLayer/Context/appDBContext.cs
from
```
namespace DataLayer;

public class appDBContext
{

}
```
to
```
using Microsoft.EntityFrameworkCore;

namespace DataLayer
{
    public class AppDbContext : DbContext
    {
        public AppDbContext(DbContextOptions<AppDbContext> options)
            : base(options)
        {
        }
    }
}
```
open PresentationLayer/Program.cs
after
```
using DataLayer;
using Microsoft.EntityFrameworkCore;
var builder = WebApplication.CreateBuilder(args);
```
add bottom code
```
#region Add Db Context
builder.Services.AddDbContext<AppDbContext>(options =>
{
    options.UseSqlServer(builder.Configuration.GetConnectionString("AppConnectionString"));
});
#endregion
```
