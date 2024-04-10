## Video 07 Helper -

### Create Entities

#### USER
##### Create class
```
cd DomainLayer/Entities/
dotnet new class --name User
```
#### Update class
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
##### Declare in Data/Context/AppDbContext.cs
