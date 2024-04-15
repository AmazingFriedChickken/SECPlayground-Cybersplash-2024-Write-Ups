

![image-20240413231309418](./assets/image-20240413231309418.png)

```
Can you find the hidden flag in the captured PCAP file. The flag pattern is network{[flag]}.
Password: secplayground
Format: network{...}
```

Challenge contain pcap file that likely to be DNS tunneling.

![image-20240416000829425](./assets/image-20240416000829425.png)

I tried grep some sample of it and decode.

![image-20240413225756668](./assets/image-20240413225756668.png)

Look like that a flag hidden. Let's extract DNS query from pcap file with wireshark.

```
tshark -r DNSLab.pcap -Y "dns" -T fields -e dns.qry.name > dns_queries.txt
```

![image-20240413231055866](./assets/image-20240413231055866.png)

I'm using Cyberchef to do the following.

1.Select only sub domain part before "".oast.me"

2.Remove duplication of result.

3.Remove .oast.me text

4.Decode from Hex.

![image-20240413231024671](./assets/image-20240413231024671.png)

![image-20240413232259420](./assets/image-20240413232259420.png)

```
Regular_expression('User defined','\\.([^.]+)\\.oast\\.me',true,true,false,false,false,false,'List capture groups')
Unique('Line feed',false)
Find_/_Replace({'option':'Regex','string':'.oast.me'},'',true,false,true,false)
From_Hex('Auto')
```



