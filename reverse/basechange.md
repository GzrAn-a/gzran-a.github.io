---
layout: default
title: Reverse Notes
permalink: /reverse
---

# Base64 换表 
### [BUGKU 题目连接](https://ctf.bugku.com/challenges/detail/id/153.html)

```python
import base64
def main():
    instr_ = "mTyqm7wjODkrNLcWl0eqO8K8gc1BPk1GNLgUpI=="
    print(base64.b64decode(instr_)) # b'\x99<\xaa\x9b\xbc#89+4\xb7\x16\x97G\xaa;\xc2\xbc\x81\xcdA>MF4\xb8\x14\xa4'
    inBase_ = "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPpQqRrSsTtUuVvWwXxYyZz0987654321/+="  # 非标准表

    Base_ =   "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789/+="  # 标准表

    # 两个表映射
    Y = dict()
    for i in range(len(inBase_)):
        Y[inBase_[i]]=Base_[i]  # 自定义表作为键、标准表作为值
    print("映射关系\n\t",Y)

    # 原始base的关系 使用 Y 字典
    outstr_ = str()
    for i in range(len(instr_)):
        outstr_ +=Y[instr_[i]]
    print("转换后\n\t",outstr_)
        # ZmxhZ3tTcGVjaWFsX0Jhc2U2NF9CeV9MaWNofQ==
    print(base64.b64decode(outstr_))
        # b'flag{Special_Base64_By_Lich}'
if __name__ == '__main__':
    main()

```

#### 输出
```shell
b'\x99<\xaa\x9b\xbc#89+4\xb7\x16\x97G\xaa;\xc2\xbc\x81\xcdA>MF4\xb8\x14\xa4'
映射关系
	 {'A': 'A', 'a': 'B', 'B': 'C', 'b': 'D', 'C': 'E', 'c': 'F', 'D': 'G', 'd': 'H', 'E': 'I', 'e': 'J', 'F': 'K', 'f': 'L', 'G': 'M', 'g': 'N', 'H': 'O', 'h': 'P', 'I': 'Q', 'i': 'R', 'J': 'S', 'j': 'T', 'K': 'U', 'k': 'V', 'L': 'W', 'l': 'X', 'M': 'Y', 'm': 'Z', 'N': 'a', 'n': 'b', 'O': 'c', 'o': 'd', 'P': 'e', 'p': 'f', 'Q': 'g', 'q': 'h', 'R': 'i', 'r': 'j', 'S': 'k', 's': 'l', 'T': 'm', 't': 'n', 'U': 'o', 'u': 'p', 'V': 'q', 'v': 'r', 'W': 's', 'w': 't', 'X': 'u', 'x': 'v', 'Y': 'w', 'y': 'x', 'Z': 'y', 'z': 'z', '0': '0', '9': '1', '8': '2', '7': '3', '6': '4', '5': '5', '4': '6', '3': '7', '2': '8', '1': '9', '/': '/', '+': '+', '=': '='}
转换后
	 ZmxhZ3tTcGVjaWFsX0Jhc2U2NF9CeV9MaWNofQ==
b'flag{Special_Base64_By_Lich}'
```
