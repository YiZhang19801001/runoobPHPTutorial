### PHP Tutorial [runoob]

***
#### variables
- 简单的声明变量`$x=2`
- 数组`$cars=array("Volvo","BMW","Toyota");`
- 对象 
```php
<?php
class Car
{
  var $color;
  function __construct($color="green") {
    $this->color = $color;
  }
  function what_color() {
    return $this->color;
  }
}
?>
```
- `var_dump`可以的类型和数值。可以用于代码调试。

#### constant 

- `define(string $name, mixed $value, bool $case_insensitive);`
- CONSTANT can be called from anywhere by `$name`

#### string

- **connect string** use `.` not `+` like C# or JavaScript
- **strlen()** return length of a string
- **strpos()** find the start index of a string in a string.
```php
<?php
    echo strpos("Hello world!","world"); //return 6.
?>
```

- more functions work with strings [String 函数](http://www.runoob.com/php/php-ref-string.html)

#### print vs echo

- print has return value and always be "1" and only output one string
- echo has not return value, and could output multiple strings in a row

#### operator 

- most operator works the same  as C# only two different ones.

  - `+` is only plus no longer connect strings

  - `intdiv`

    ```php
    <?php
    var_dump(intdiv(10, 3));
    ?>
    ```

    `return value will be int(3)`

#### Array

- **Create** 

  ```php
  $cars=array("Volvo","BMW","Toyota");
  ```

- **Count()** to get length of an array.

- **key-value pair**

  ```php
  <?php
  $age=array("Peter"=>"35","Ben"=>"37","Joe"=>"43");
  echo "Peter is " . $age['Peter'] . " years old.";
  ?>
  ```

- **iterate array**

  ```php
  <?php
  $age=array("Peter"=>"35","Ben"=>"37","Joe"=>"43");
   
  foreach($age as $x=>$x_value)
  {
      echo "Key=" . $x . ", Value=" . $x_value;
      echo "<br>";
  }
  ?>
  ```

- **sort()**
  - sort() - 对数组进行升序排列
  - rsort() - 对数组进行降序排列
  - asort() - 根据关联数组的值，对数组进行升序排列
  - ksort() - 根据关联数组的键，对数组进行升序排列
  - arsort() - 根据关联数组的值，对数组进行降序排列
  - krsort() - 根据关联数组的键，对数组进行降序排列
- **superglobals** 
  - $GLOBALS
  - $_SERVER
  - $_REQUEST
  - $_POST
  - $_GET
  - $_FILES
  - $_ENV
  - $_COOKIE
  - $_SESSION

