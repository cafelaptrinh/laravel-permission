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


# Tương tác giữa pemrmission và role
