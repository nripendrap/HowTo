## Different ways of checking null
Classic
```
if(x == null) 
{
    throw new ArgumentNullException((nameof(x)));
}
```
With C# 7.0
```
if(x is null) 
{
    throw new ArgumentNullException(nameof(x));
}
```
```
_ = x ?? throw new ArgumentNullException(nameof(x));
``` 
## Checking not null
```
x != null
!(x is null)
x is object
```

With C# 9.0, we can write null and not null checks
```
if(x is null) { }
if(x is not null) { }
```
## What is the difference between "x is null" and "x == null"

Operator overloading

Comparison operator like == can be overloaded

if the == operator is overloaded to use custom implementation in a user-defined type, when comparing checking equality. x == null will run the overloaded == operator whereas "x is null" use direct reference comparison.

https://stackoverflow.com/questions/40676426/what-is-the-difference-between-x-is-null-and-x-null


### Why nameof(x)

