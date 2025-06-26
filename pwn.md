```cpp
int __cdecl main(int argc, const char **argv, const char **envp)
{
  char s[128]; // [esp+0h] [ebp-8Ch] BYREF
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
