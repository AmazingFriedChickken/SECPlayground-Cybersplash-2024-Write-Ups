![image-20240414185733221](./assets/image-20240414185733221.png)

The challenge contains two files. It was a machine memory dump.

![image-20240414184931101](./assets/image-20240414184931101.png)

I'm using Volatility3 to analyze the memory.

```
git clone https://github.com/volatilityfoundation/volatility3.git
```

![image-20240414185148677](./assets/image-20240414185148677.png)

I tried to enumerate files and found that the machine has Python installed.

```
python3 vol.py -f ../JOHN-PC-20240402-164218.dmp windows.filescan.FileScan
```

![image-20240414185419813](./assets/image-20240414185419813.png)

I'm looking for Python source code using the grep command.

```
python3 vol.py -f ../JOHN-PC-20240402-164218.dmp windows.filescan.FileScan | grep .py
```

![image-20240414185458212](./assets/image-20240414185458212.png)

![image-20240414185519988](./assets/image-20240414185519988.png)

Now I've found suspicious Python source code. I have to dump it by referencing the physical address on the left side, then use the DumpFiles plugin to extract the file.

```
python3 vol.py -f ../JOHN-PC-20240402-164218.dmp windows.dumpfiles.DumpFiles --physaddr 0x7e70fdd0
```

![image-20240414185609986](./assets/image-20240414185609986.png)