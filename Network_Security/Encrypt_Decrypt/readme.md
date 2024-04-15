![image-20240415215808052](./assets/image-20240415215808052.png)

```
Can you find the hidden flag in the captured PCAP file. The flag pattern is network{[flag]}.
Password: secplayground
Format: network{...}
```

The Challenge contain 2 file.

textfile : Contain a Secret log filename

TLSLab.pcapng : Contain a TLS 1.3 traffic

![image-20240415220127021](./assets/image-20240415220127021.png)

![image-20240415220245996](./assets/image-20240415220245996.png)

I need to decrypt TLS traffic. In order to do that, I Import textfile in wireshark.

https://www.comparitech.com/net-admin/decrypt-ssl-with-wireshark/

![image-20240415220520364](./assets/image-20240415220520364.png)

![image-20240415220540611](./assets/image-20240415220540611.png)

```
network{t1sd3crypt}
```

