# Cách Tạo, gán pemrmission và role

```php
use CafeLT\Permission\Models\Role;
use CafeLT\Permission\Models\Permission;


      //Tạo Role :
          $role=Role::create([
              'name'=>'admin',
              'display_name'=>'Quản Trị Viên',
              'guard_name'=>'web'
              ]);
              
       // Tạo Permission
          $permission=Pẻmission::create([
              'name'=>'dashboard',
              'display_name'=>'Đăng nhập dashboard',
              'guard_name'=>'web'
              ]);
```
    **Trong đó :** 

                name : Tên role muốn tạo

               display_name : Tên Role muốn Hiển Thị
               
               guard_name : Tên guard (mặc định là web)
               

### Gán permission vào role
```php
      $role->givePermissionTo($permission);
      //hoặc
      $permission->assignRole($role);
```

### Đồng bộ hóa nhiều permission cho 1 role
```php
    $role->syncPermissions($permissions);
```

### Đồng bộ hóa 1 permission cho nhiều role
```php
    $permission->syncRoles($roles);
```

### Xóa permission của 1 role
```php
    $role->revokePermissionTo($permission);
    //Hoặc
    $permission->removeRole($role);
```


# Tương tác giữa user và role
```php
//Lấy tất cả các permission mà user có
$user->getAllPermissions()


// kiểm tra xem user có permission này không
$user->hasPermissionTo($permission->name)
// Hoặc
$user->hasPermissionTo($permission->id)

//Kiểm tra xem user có nhiều permission này không
$user->hasAnyPermission([$permission1->name,$permission2->name,$permission3->name])
//hoặc
$user->hasAnyPermission([$permission1->id,$permission2->id,$permission3->id])
//hoặc
$user->hasAnyPermission([$permission1->name,$permission2->id,$permission3->id])

ý tôi là bạn có thể truyền id hoặc name của permission tùy ý
```

### Gán role cho user
```php
//gán 1 role cho 1 user
$user->assignRole('admin');
//gán nhiều role cho 1 user
$user->assignRole(['admin','member']);
```

### Xóa role của user
```php
//xóa 1 role
$user->removeRole('admin')
//xóa nhiều role
$user->removeRole(['admin','member'])
```

### Đồng bộ hóa role cho user
```php
$user->syncRoles('admin')
//hoặc
$user->syncRoles(['admin','member'])
```

### Kiểm tra xem user có role này không
```php
//1 role
$user->hasRole('admin')
//nhiều role
$user->hasAnyRole(['admin','member'])
//hoặc
$user->hasAnyRole('admin','member')
//hoặc
$user->hasAllRoles(Role::all())

```
