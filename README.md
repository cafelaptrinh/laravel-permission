# Phân Quyền laravel


[![Latest Version on Packagist](https://img.shields.io/packagist/v/cafelaptrinh/laravel-role.svg?style=flat-square)](https://packagist.org/packages/cafelaptrinh/laravel-role)
[![Total Downloads](https://img.shields.io/packagist/dt/cafelaptrinh/laravel-role.svg?style=flat-square)](https://packagist.org/packages/cafelaptrinh/laravel-role)

### Cài đặt

# Bước 1
Sử dụng câu lệnh composer require:

```bash
composer require cafelaptrinh/laravel-role
```


# Bước 2
Tiếp theo chạy lệnh:
``` php
    php artisan vendor:publish --provider="CafeLT\Permission\PermissionServiceProvider"
```
Lệnh này sẽ tạo config, migration và seeder

# Bước 3
Chạy tiếp lệnh migrate để tạo table database cần thiết:
```php
    php artisan migrate
```


# Bước 4
\* *Nếu phiên bản laravel của bạn từ laravel 5.5 trở lên thì bỏ qua bước này.*

Sau khi chạy composer xong tiến hành vào file config/app.php và add provider:

```php
'providers'=>[
    CafeLT\Permission\PermissionServiceProvider::class,
]
```

# Bước 5
Vào model người dùng thêm lệnh sau:
 \* *laravel mặc định là App\Users.*
```php
<?php
namespace App;

use CafeLT\Permission\Traits\HasRoles;
...

class User extends Authenticatable
{
...

use hasRole;

...
}

```


Vậy là đã cài thành công ! Giờ hãy chọn các mục dưới đây:

[Cách dùng Role](https://github.com/cafelaptrinh/laravel-role/blob/master/docs/use-role.md)

[Cách dùng Role trong Blade laravel](https://github.com/cafelaptrinh/laravel-role/blob/master/docs/role-blade.md)
