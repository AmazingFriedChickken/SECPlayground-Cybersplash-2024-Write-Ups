![image-20240414082557127](./assets/image-20240414082557127.png)

The challenge contains one file. It was a machine memory dump.

![image-20240415005031837](./assets/image-20240415005031837.png)

```
python3 vol.py -f ../something_secret_inside.dmp windows.filescan.FileScan | grep .txt
```

![image-20240415005112236](./assets/image-20240415005112236.png)

![image-20240415005148501](./assets/image-20240415005148501.png)

```
python3 vol.py -f ../something_secret_inside.dmp windows.dumpfiles.DumpFiles --physaddr 0x7e9c7da0
```

![image-20240415004856808](./assets/image-20240415004856808.png)

