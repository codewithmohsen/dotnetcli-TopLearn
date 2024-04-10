## Video 07 Helper - ایجاد مدل و Repository مربوط به کاربران


### Create Entities

#### USER
##### 1. Create class
```
cd DomainLayer/Entities/
dotnet new class --name User
```
#### 2. Update class
open User.cs and updte
```
namespace DomainLayer;
public class User
{

}
```
to
```
using System.ComponentModel.DataAnnotations;

namespace DomainLayer;

public class User
{
    [Key]
    public int UserId { get; set; }
    [Display(Name = "ایمیل")]
    [Required(ErrorMessage = "لطفا {0} را وارد کنید")]
    [MaxLength(350, ErrorMessage = "حداکثر کاراکتر مجاز {1} میباشد")]
    public string Email { get; set; }
    [Display(Name = "کلمه عبور")]
    [Required(ErrorMessage = "لطفا {0} را وارد کنید")]
    [MaxLength(350, ErrorMessage = "حداکثر کاراکتر مجاز {1} میباشد")]
    public string Password { get; set; }
    [Display(Name = "نام کاربری")]
    [Required(ErrorMessage = "لطفا {0} را وارد کنید")]
    [MaxLength(350, ErrorMessage = "حداکثر کاراکتر مجاز {1} میباشد")]
    public string UserName { get; set; }
}
```
##### 3. Declare in Data/Context/AppDbContext.cs
update 
'''
using DomainLayer;
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
'''
to
'''
using DomainLayer;
using Microsoft.EntityFrameworkCore;
namespace DataLayer
{
    public class AppDbContext : DbContext
    {
        public AppDbContext(DbContextOptions<AppDbContext> options)
            : base(options)
        {
        }
        #region Users
        public DbSet<User> Users { get; set; }
        #endregion
    }
}
'''
##### 4. Migrate Database
