![image-20240413234724762](./assets/image-20240413234724762.png)

The challenge contains one JPG file.

![steganography_secplayground](./assets/steganography_secplayground.jpg)

I'm using this tool to find a hidden file.

https://github.com/DominicBreuker/stego-toolkit

Create a data directory and copy steganography_secplayground.jpg into it. Then use a Docker command to mount and shell into it.

```bash
docker run -v /home/kali/Desktop/CTF/Cyptography/1-Something_behind/steganography_secplayground/data:/data -it dominicbreuker/stego-toolkit /bin/bash
```

Execute the command below to automatically analyze the file.

```bash
stegoveritas steganography_secplayground.jpg
```

![image-20240413234711349](./assets/image-20240413234711349.png)

![image-20240414184101064](./assets/image-20240414184101064.png)

![image-20240414184135773](./assets/image-20240414184135773.png)

