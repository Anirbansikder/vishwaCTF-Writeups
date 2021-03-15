# Solution

The challenge description said something about robots.

So went to https://uwu.vishwactf.com/robots.txt

But this time it was a directory which had a source code -> 

https://uwu.vishwactf.com/robots/?showThem

```php
<!DOCTYPE HTML>
<?php
  require("cyberflagster.php");  
  $try; //1
  $function; //5
  if (isset($_GET['showThem'])) {
   
    highlight_file(__FILE__);
   
    die();
  
  }
   $reach;//3
  if (isset($_GET['php_is_hard'])) {
  
    $you_enter = $_GET['php_is_hard'];
  
    $we_enter = 'suzuki_harumiya';
  
    $the_final_one = preg_replace(
    
      "/$we_enter/", '', $you_enter);
  
      if ($the_final_one === $we_enter) {
  
        open_up();
    }
  }
  $to; //2
  $open_up;//4
?>

<html>
  <head>
    <title>VishwaCTF-mini | web-php-1</title>
  </head>
  <body style="background-color:#121212">
  <h1>Try Solving this normie<h1>
  <a target="_blank" href="?showThem"><h3>Source Code</h3></a>

  </body>
</html>
```

Now preg_replace replaces every thing of you_enter that matches with 'suzuki_harumiya' with ''.

so we can trick it and get the flag by sending a get request of ->

https://uwu.vishwactf.com/robots/?php_is_hard=suzuki_suzuki_harumiyaharumiya  which yields

``` Flag : vishwaCTF{well_this_was_a_journey} ```