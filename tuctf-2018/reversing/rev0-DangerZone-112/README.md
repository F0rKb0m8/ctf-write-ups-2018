# DangerZone [Reverse 112 points]

### Chall's description
Difficulty: easy
Legend says, this program was written by Kenny Loggins himself.

#### File given for the chall
* [dangerzone.pyc](./dangerzone.pyc)

## Solution (A)
We started importing the .pyc in python then we inspected it with dir().
```python
>>> import dangerzone
>>> dir(dangerzone)
['__builtins__', '__doc__', '__file__', '__name__', '__package__', 'b32decode', 'base64', 'main', 'reverse', 'reversePigLatin', 'rot13']
>>>
```
So, we tried to run the main module's main procedure
```python
>>> dangerzone.main()
Something Something Danger Zone
'=YR2XYRGQJ6KWZENQZXGTQFGZ3XCXZUM33UOEIBJ'
```

We noticed that it is a reverted (link to)base64 encoded string.
After some tests, with the help of the other module's functions, we found the flag:
```python
>>> dangerzone.reversePigLatin(dangerzone.rot13(dangerzone.b32decode(dangerzone.reverse(dangerzone.main()))))
Something Something Danger Zone
u'TUCTF{r3d_l1n3_0v3rl04d}'
```

## Solution (B)
Another way to solve this chall is to use [uncompyle6](https://github.com/rocky/python-uncompyle6).
Running the following command, `main.py` will contain the original code of dangerzone.
```bash
$ uncompyled6 ./dangerzone.pyc > main.py
```

#### `main.py` code:
```python
import base64

def reverse(s):
    return s[::-1]

def b32decode(s):
    return base64.b32decode(s)

def reversePigLatin(s):
    return s[-1] + s[:-1]

def rot13(s):
    return s.decode('rot13')

def main():
    print 'Something Something Danger Zone'
    return '=YR2XYRGQJ6KWZENQZXGTQFGZ3XCXZUM33UOEIBJ'

if __name__ == '__main__':
    s = main()
    print s
```

Then we change the main function with the same code write on the Solution(A) to
obtain the flag.


# The Flag:
    TUCTF{r3d_l1n3_0v3rl04d}
