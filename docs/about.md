# role trong blade
### Sử dụng can của laravel
```php
@can('dashboard')
...
@endcan
```

### kiểm tra role
```php
@role('writer')
    tôi là writer!
@else
    tôi không phải writer...
@endrole
```
Or
```php
@hasrole('writer')
    tôi là writer!
@else
    tôi không phải writer...
@endhasrole
```

###Kiểm tra nhiều role
```php
@hasanyrole('writer|admin')
    Tôi là writer hoặc admin!
@else
    tôi không phải
@endhasanyrole



@hasallroles('writer|admin')
    tôi là writer và admin!
@else
    tôi không phải
@endhasallroles



@unlessrole('admin')
    tôi không phải admin
@else
    tôi là admin
@endunlessrole
```
