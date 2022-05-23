+++
title = "Markdown test"
date = "1333-01-01"
+++

# H1
## H2
### H3
#### H4
##### H5

**Bold Text**  
*Italic text*  
~~Strikethrough~~  
__Underline__  
***Bold Italics***  
__*Underline Italics*__  
__**Underline Bold**__  
__***Underline Bold Italics***__

- My
- Cool
- List
  

* My
* Other
* List

## Code Blocks

```py
def my_function_call(my_variable):
    print(f"{my_variable=}")

if my_cool_statement == True:
    print("Hello World")
else:
    my_function_call("yeet")
```
```cpp
#include <iostream>
#include <string>

using namespace std;

int main()
{

    for (int i = 1; i < 101; i++) {
        string yeet = "";
       
        if (i % 3 == 0) yeet += "Fizz";
        if (i % 5 == 0) yeet += "Buzz";
        
        if (yeet != "") cout << yeet << endl;
        else cout << i << endl;
    }
    
    return 0;
}
```


## Quote Tag
> I made this thing I swear 

Every developer ever

> It even supports multiple lines aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa

## Code parts?
My `cool` text that includes `stuff`

## Links
[Fizz Buzz](https://en.wikipedia.org/wiki/Fizz_buzz) is actully a good way to learn coding  
1, 2, Fizz, 4, Buzz, Fizz, 7, 8, Fizz, Buzz, 11, Fizz, 13, 14, [Fizz Buzz](https://en.wikipedia.org/wiki/Fizz_buzz), 16, 17, Fizz, 19, Buzz, Fizz, 22, 23, Fizz, Buzz, 26, Fizz, 28, 29, [Fizz Buzz](https://en.wikipedia.org/wiki/Fizz_buzz), 31, 32, Fizz, 34, Buzz, Fizz

## Image
![](https://code.kx.com/q/img/fizzbuzz.png)