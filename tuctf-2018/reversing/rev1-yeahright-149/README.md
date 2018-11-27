# yeahright [Reverse 149 points]

### Chall's description
```
Difficulty: very easy
What an insensitive little program.
Show it who's boss!

nc 18.224.3.130 12345
```

#### File given for the chall
* [yeahright](./yeahright)
* [flag](./flag)

## Solution
First we tried to check the binary with `strings` command to see if we could find something useful.
```bash
$ strings yeahright | less
```

Luckely, we immediately found a password required by the program!

#### output:
```bash
[...]
GLIBC_2.2.5
AWAVA
AUATL
[]A\A]A^A_
7h3_m057_53cr37357_p455w0rd_y0u_3v3r_54w    <===
*Ahem*... password? 
yeahright!
/bin/cat ./flag
;*3$"
[...]
```

We tried to insert the password ('7h3\_m057\_53cr37357\_p455w0rd\_y0u\_3v3r\_54w') as the program's input, and we noticed that it executes the ```/bin/cat ./flag```.
Running this on the server, cat the real flag!


# The Flag:
    TUCTF{n07_my_fl46_n07_my_pr0bl3m}
