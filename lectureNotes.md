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

- **include & require**

  `include` will continue run the code, `require` will stop the code, when errors occur.

- **fopen** to open file

  ```php
  <html>
  <body>
  
  <?php
  $file=fopen("welcome.txt","r");
  ?>
  
  </body>
  </html>
  ```

  `r` read only from begin, `w` write only or create, `a` append or create, `x` write only or return false

  ```php
  <html>
  <body>
  
  <?php
  $file=fopen("welcome.txt","r") or exit("Unable to open file!");
  ?>
  
  </body>
  </html>
  ```


- `fclose` close file

  ```php
  <?php
  $file = fopen("test.txt","r");
  
  //执行一些代码
  
  fclose($file);
  ?>
  ```

- `fgetc()` read file line by line

  ```php
  <?php
  $file=fopen("welcome.txt","r") or exit("无法打开文件!");
  while (!feof($file)) //check get the tail of file or not.
  {
      echo fgetc($file);
  }
  fclose($file);
  ?>
  ```

- `upload()` 

  ```php
  <html>
  <head>
  <meta charset="utf-8">
  <title>菜鸟教程(runoob.com)</title>
  </head>
  <body>
  
  <form action="upload_file.php" method="post" enctype="multipart/form-data">
      <label for="file">文件名：</label>
      <input type="file" name="file" id="file"><br>
      <input type="submit" name="submit" value="提交">
  </form>
  
  </body>
  </html>
  ```

  ```php
  <?php
  // 允许上传的图片后缀
  $allowedExts = array("gif", "jpeg", "jpg", "png");
  $temp = explode(".", $_FILES["file"]["name"]);
  echo $_FILES["file"]["size"];
  $extension = end($temp);     // 获取文件后缀名
  if ((($_FILES["file"]["type"] == "image/gif")
  || ($_FILES["file"]["type"] == "image/jpeg")
  || ($_FILES["file"]["type"] == "image/jpg")
  || ($_FILES["file"]["type"] == "image/pjpeg")
  || ($_FILES["file"]["type"] == "image/x-png")
  || ($_FILES["file"]["type"] == "image/png"))
  && ($_FILES["file"]["size"] < 204800)   // 小于 200 kb
  && in_array($extension, $allowedExts))
  {
      if ($_FILES["file"]["error"] > 0)
      {
          echo "错误：: " . $_FILES["file"]["error"] . "<br>";
      }
      else
      {
          echo "上传文件名: " . $_FILES["file"]["name"] . "<br>";
          echo "文件类型: " . $_FILES["file"]["type"] . "<br>";
          echo "文件大小: " . ($_FILES["file"]["size"] / 1024) . " kB<br>";
          echo "文件临时存储的位置: " . $_FILES["file"]["tmp_name"] . "<br>";
          
          // 判断当期目录下的 upload 目录是否存在该文件
          // 如果没有 upload 目录，你需要创建它，upload 目录权限为 777
          if (file_exists("upload/" . $_FILES["file"]["name"]))
          {
              echo $_FILES["file"]["name"] . " 文件已经存在。 ";
          }
          else
          {
              // 如果 upload 目录不存在该文件则将文件上传到 upload 目录下
              move_uploaded_file($_FILES["file"]["tmp_name"], "upload/" . $_FILES["file"]["name"]);
              echo "文件存储在: " . "upload/" . $_FILES["file"]["name"];
          }
      }
  }
  else
  {
      echo "非法的文件格式";
  }
  ?>
  ```

- **PHP Cookies**
  - **注释：**setcookie() 函数必须位于 <html> 标签之前。